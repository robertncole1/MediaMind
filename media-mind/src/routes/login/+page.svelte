<script lang="ts">
  import { auth } from '$lib/firebase';
  import { signInWithEmailAndPassword } from 'firebase/auth';

  let email = '';
  let password = '';
  let errorMsg = '';

  async function handleLogin() {
    try {
      await signInWithEmailAndPassword(auth, email, password);
      errorMsg = '';
      alert('Login successful!');
    } catch (error) {
      errorMsg = (error as Error).message;
    }
  }
</script>

<h1>Login</h1>
<input type="email" bind:value={email} placeholder="Email" />
<input type="password" bind:value={password} placeholder="Password" />
<button on:click={handleLogin}>Login</button>

{#if errorMsg}
  <p style="color: red">{errorMsg}</p>
{/if}
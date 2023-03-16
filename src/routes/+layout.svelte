<script>
	// @ts-nocheck
	import { page } from '$app/stores';
	import { goto } from '$app/navigation';
	import '../app.css';
	import Navbar from '$lib/components/Navbar.svelte';
	import Sidebar from '$lib/components/Sidebar.svelte';
	$: {
		if (!$page.data.user) {
			goto('/auth/login');
		}
	}
	$:console.log($page.data.user);
</script>

<svelte:head>
	<link
		rel="stylesheet"
		href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/css/bootstrap.min.css"
	/>
</svelte:head>
<main id="content">
	{#if $page.data.user}
		<Navbar />
		<Sidebar />
		<main class="mt-16 ml-[16.5rem]">
			<slot />
		</main>
	{:else}
		<slot />
	{/if}
	
</main>

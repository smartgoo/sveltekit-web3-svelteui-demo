<script lang="ts">
	import { Stack, Button, Divider } from '@svelteuidev/core';
	import { connected, selectedAccount } from 'svelte-web3';
	import { mobile } from '$lib/stores';
	import ConnectMetaMask from './ConnectMetaMask.svelte';

	import { goto } from '$app/navigation';
</script>

<Stack spacing="xs">
	{#if $mobile}
		<ConnectMetaMask />
	{/if}

	<Button
		variant="light"
		color="gray"
		ripple
		on:click={() => {
			goto('/');
		}}
	>
		Home
	</Button>

	<Divider label="Search" labelPosition="center" />
	<Button
		variant="light"
		color="gray"
		ripple
		on:click={() => {
			goto('/block/search');
		}}
	>
		Block Search
	</Button>
	<!-- <Button
		variant="light"
		color="gray"
		ripple
		on:click={() => {
			goto('/address/search');
		}}
	>
		Address Search
	</Button>
	<Button
		variant="light"
		color="gray"
		ripple
		on:click={() => {
			goto('/transaction/search');
		}}
	>
		Transaction Search
	</Button> -->

	<Divider label="Utilities" labelPosition="center" />
	<Button
		variant="light"
		color="gray"
		ripple
		on:click={() => {
			goto('/address/checksum');
		}}
	>
		Address Checksum
	</Button>

	{#if $connected}
		<Divider label="My Account" labelPosition="center" />
		<Button
			variant="light"
			color="gray"
			ripple
			on:click={() => {
				goto('/address/' + $selectedAccount);
			}}
		>
			Balance
		</Button>
	{/if}
</Stack>

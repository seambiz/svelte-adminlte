<script>
	import {createEventDispatcher} from "svelte"

	const dispatch = createEventDispatcher()

	export let header = ""
	export let closeable = true
	export let level = ""
	export let icon = ""

	function alertClosed() {
		dispatch("closed")
	}

</script>

<div class="alert alert-{level}"
class:alert-dismissible = {closeable}
>
{#if closeable}
	<button type="button" class="close" data-dismiss="alert" aria-hidden="true" on:click={alertClosed}>×</button>
{/if}
<h4><i class="icon fa fa-{icon}"></i> {header}</h4>
<slot />
</div>
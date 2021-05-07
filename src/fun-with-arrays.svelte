<script>
	import { fade, scale } from 'svelte/transition';
	import { flip } from 'svelte/animate';
 let array = [0, 1, 2, 3, 4];

 let returned = '';

 function pop() {
	 returned = array.pop();
	 array=array;
 }

 function push() {
	 if (array.length > 0) {
	 	returned = array.push(array[array.length - 1] + 1);
	 	array = array
	 } else {
		returned = array.push(0);
		array = array;
	 }
 }

 function shift() {
	 returned = array.shift();
	 array = array;
 }

 function unshift() {
	 if (array.length > 0) {
		returned = array.unshift(array[0] - 1);
		array = array;
	 } else {
		returned = array.unshift(0);
		array = array; 
	 }
 }

</script>
<h2>array:</h2>
<div class= "array">
	{#each array as element, i (element)}
		<div animate:flip="{{ duration: 300 }}" out:scale="{{ duration: 250 }}" in:scale="{{ duration: 250 }}" class="element">{element}</div>
	{/each}
</div>
<h2>returned:</h2>

<div class="returned">
	{returned}
</div>

<button on:click={pop}>pop</button>
<button on:click={push}>push</button>
<button on:click={shift}>shift</button>
<button on:click={unshift}>unshift</button>

<style>
	h2 {
		font-family: var(--font-family-body);
		font-weight: 600;
		font-size: var(--font-size-large);
		margin: var(--s2) 0 var(--s1);
	}

	.array {
		display: flex;
		height: 3em;
	}

	.element {
		width: 3em;
		height: 3em;
		background-color: #5F8;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 2px solid black;
	}
	
	.element + .element {
		margin-left: .25em;
	}

	.returned {
		width: 3em;
		height: 3em;
		background-color: #FF5599;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 2px solid black;
		margin-bottom: 2rem;
	}

	button {
		color: #000;
		background-color: #BB99FF;
		padding: .75em 1.5em;
		border: 2px solid black;
		border-radius: .25em;
		box-shadow: -.25em .25em 0 #000;
		cursor: pointer;
	}

	button + button { margin-left: .5em}
</style>
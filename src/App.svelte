<script>
    import ContactCard from "./ContactCard.svelte";

	let name = 'Been';
    let title = '';
    let image = '';
    let description = '';
    let age = 32;

    $: uppercaseName = name.toUpperCase();

    $: console.log(name);

    $: if (name === 'WonBeen') {
        age = 30;
    }

    function incrementAge() {
        age += 1;
    }

    function changeName() {
        name = 'WonBeen';
    }

    function nameInput(event) {
        const enteredValued = event.target.value;
        name = enteredValued;
    }

    let uppercaseName;
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {uppercaseName}!, My age {age}!</h1>
<button on:click="{incrementAge}">Change Age</button>
<!--<button on:click="{changeName}">Change Name</button>-->
<!--<input type="text" value="{name}" on:input="{nameInput}">-->
<input type="text" bind:value="{name}">
<input type="text" bind:value="{title}">
<input type="text" bind:value="{image}">
<textarea rows="3" bind:value="{description}"></textarea>

<ContactCard
        userName="{name}"
        jopTitle="{title}"
        {description}
        userImage="{image}"
/>

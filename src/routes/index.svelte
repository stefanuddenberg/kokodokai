<svelte:head>
	<title>Kokodokai</title>
</svelte:head>

<h1>Rise Above</h1>

<div class="center">
	<p>
		you must rise above<br />
		the gloomy clouds<br />
		covering the mountaintop<br />
		otherwise, how will you<br />
		ever see the brightness?
	</p>
	<p>
		&mdash; <a href="https://hellopoetry.com/poem/66443/rise-above/">Ryōkan Taigu</a>
	</p>
</div>


<ul>
	{#each posts as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<li>
			<a rel='prefetch' href='{post.slug}'>
				{#if post.image}
					<figure>
						<span><img src="{post.image}" alt="" /></span>
					</figure>
				{/if}
				{post.title}
			</a>
		</li>
	{/each}
</ul>

<style>
	figure img {
		max-width: 202px;
	}

	figure span {
		align-items: flex-end;
		display: -webkit-box;
		display: -moz-box;
		display: -ms-flexbox;
		display: -webkit-flex;
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		height: 202px;
		width: 202px;
	}

	h1 {
		font-size: 2.8em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0.25em 0 0.0625em;
	}

	ul {
		align-items: flex-start;
		display: -webkit-box;
		display: -moz-box;
		display: -ms-flexbox;
		display: -webkit-flex;
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		line-height: 1.5;
		list-style: none;
		margin: 0 0 1em 0;
		padding: 0;
	}

	ul li {
		list-style-type: none;
		padding: 11px;
		text-align: center;
		width: 202px;
	}

	li a {
		display: block;
	}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>


<script context="module">
	export async function preload({ params, query }) {
			return this.fetch(`index.json`).then(r => r.json()).then(posts => {
				return { posts };
			});
		}
</script>

<script>
	export let posts;
</script>

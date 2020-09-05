<script>
  import { createEventDispatcher } from "svelte";

  let selected = false;

  const dispatch = createEventDispatcher();

  const select = (category) => {
    console.log("selected", category);
    selected = true;
    dispatch("select", { category });
  };
  const categories = [
    {
      label: "Actors",
      slug: "actors",
    },
    {
      label: "Athletes",
      slug: "athletes",
    },
    {
      label: "Comedians",
      slug: "comedians",
    },
    {
      label: "Creators",
      slug: "creators",
    },
    {
      label: "Models",
      slug: "models",
    },
    {
      label: "Musicians",
      slug: "musicians",
    },
    {
      label: "Reality TV",
      slug: "reality-tv",
    },
  ];
</script>

<style>
  h1 {
    text-transform: uppercase;
    font-size: min(12vw, 4em);
    font-weight: 100;
    margin: 0 0 0.5em 0;
  }
  .logo {
    display: inline-block;
    background: url(/icons/compare.svg) 50% 50% no-repeat;
    background-size: 100% 100%;
    width: 0.8em;
    top: 0.05em;
    transform: scale(1.4);
    left: 0.02em;
    text-indent: -9999px;
  }
  p {
    max-width: 24em;
    margin: 0 auto 1em auto;
  }
  .categories {
    width: 100%;
    max-width: 26em;
    margin: 0 auto;
    text-align: center;
  }
  button {
    padding: 1em;
    display: block;
    margin: 0 0 0.2em 0;
    width: 100%;
  }
  @media (min-width: 640px) {
    button {
      display: inline;
      margin: 0 0.2em 0.4em 0.2em;
      width: auto;
    }
  }
</style>

<header>
  <h1>CameoP<span class="logo">a</span>rison</h1>
  <p>
    On <a href="https://cameo.com">cameo.com</a>, you can buy personalised video
    clips from everyone from Lindsay Lohan to Ice T.
  </p>
  <p>But who commands the highest price?</p>
</header>

<p>Pick a category to play a game:</p>
<div class="categories">
  {#each categories as category}
    <button
      disabled={selected}
      on:click={() => select(category.slug)}>{category.label}</button>
  {/each}
</div>

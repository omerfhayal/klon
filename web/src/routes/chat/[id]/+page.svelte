<script lang="ts">
  import { navigating } from "$app/stores";
  import type { PageData } from "./$types";

  export let data: PageData;

  const questions = data.props.questions ?? [];
</script>

<div class="max-w-4xl mx-auto">
  {#each questions as question}
    <div class="chat chat-end">
      <div class="chat-bubble chat-bubble-primary">
        {question.question}
      </div>
    </div>
    <div class="chat chat-start">
      <div class="chat-bubble chat-bubble-success">
        {question.answer}
      </div>
    </div>
  {/each}

  <form method="POST" class="form-control items-center mt-3">
    <textarea
      name="question"
      class="textarea textarea-bordered h-24 w-full"
      placeholder="Why is the sky blue?"
    />
    <button
      class={"btn btn-primary max-w-lg m-3" + ($navigating ? "loading" : "")}
    >
      Ask your question
    </button>
  </form>
</div>
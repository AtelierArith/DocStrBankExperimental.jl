```
aihelp!"user_question"[model_alias] -> AIMessage
```

The `aihelp!""` string macro is used to continue a previous conversation with the AI model. 

It appends the new user prompt to the last conversation in the tracked history (in `AIHelpMe.CONV_HISTORY`) and generates a response based on the entire conversation context. If you want to see the previous conversation, you can access it via `AIHelpMe.CONV_HISTORY`, which keeps at most last `PromptingTools.MAX_HISTORY_LENGTH` conversations.

It does NOT provide new context from the documentation. To do that, start a new conversation with `aihelp"<question>"`.

## Arguments

  * `user_question` (String): The follow up question to be added to the existing conversation.
  * `model_alias` (optional, any): Specify the model alias of the AI model to be used (see `PT.MODEL_ALIASES`). If not provided, the default model is used.

## Returns

`AIMessage` corresponding to the new user prompt, considering the entire conversation history.

## Example

To continue a conversation:

```julia
# start conversation as normal
aihelp"How to create a dictionary?" 

# ... wait for reply and then react to it:

# continue the conversation (notice that you can change the model, eg, to more powerful one for better answer)
aihelp!"Can you create it from named tuple?"gpt4t
# AIMessage("Yes, you can create a dictionary from a named tuple ...")
```

## Usage Notes

  * This macro should be used when you want to maintain the context of an ongoing conversation (ie, the last `ai""` message).
  * It automatically accesses and updates the global conversation history.
  * If no conversation history is found, it raises an assertion error, suggesting to initiate a new conversation using `ai""` instead.

## Important

Ensure that the conversation history is not too long to maintain relevancy and coherence in the AI's responses. The history length is managed by `MAX_HISTORY_LENGTH`.

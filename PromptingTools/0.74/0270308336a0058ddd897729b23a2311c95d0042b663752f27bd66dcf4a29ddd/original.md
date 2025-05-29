```
aiscan([prompt_schema::AbstractOpenAISchema,] prompt::ALLOWED_PROMPT_TYPE; 
image_url::Union{Nothing, AbstractString, Vector{<:AbstractString}} = nothing,
image_path::Union{Nothing, AbstractString, Vector{<:AbstractString}} = nothing,
image_detail::AbstractString = "auto",
attach_to_latest::Bool = true,
verbose::Bool = true, api_key::String = OPENAI_API_KEY,
    model::String = MODEL_CHAT,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    http_kwargs::NamedTuple = (;
        retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), 
    api_kwargs::NamedTuple = = (; max_tokens = 2500),
    kwargs...)
```

Scans the provided image (`image_url` or `image_path`) with the goal provided in the `prompt`.

Can be used for many multi-modal tasks, such as: OCR (transcribe text in the image), image captioning, image classification, etc.

It's effectively a light wrapper around `aigenerate` call, which uses additional keyword arguments `image_url`, `image_path`, `image_detail` to be provided.   At least one image source (url or path) must be provided.

# Arguments

  * `prompt_schema`: An optional object to specify which prompt template should be applied (Default to `PROMPT_SCHEMA = OpenAISchema`)
  * `prompt`: Can be a string representing the prompt for the AI conversation, a `UserMessage`, a vector of `AbstractMessage` or an `AITemplate`
  * `image_url`: A string or vector of strings representing the URL(s) of the image(s) to scan.
  * `image_path`: A string or vector of strings representing the path(s) of the image(s) to scan.
  * `image_detail`: A string representing the level of detail to include for images. Can be `"auto"`, `"high"`, or `"low"`. See [OpenAI Vision Guide](https://platform.openai.com/docs/guides/vision) for more details.
  * `attach_to_latest`: A boolean how to handle if a conversation with multiple `UserMessage` is provided. When `true`, the images are attached to the latest `UserMessage`.
  * `verbose`: A boolean indicating whether to print additional information.
  * `api_key`: A string representing the API key for accessing the OpenAI API.
  * `model`: A string representing the model to use for generating the response. Can be an alias corresponding to a model ID defined in `MODEL_ALIASES`.
  * `return_all::Bool=false`: If `true`, returns the entire conversation history, otherwise returns only the last message (the `AIMessage`).
  * `dry_run::Bool=false`: If `true`, skips sending the messages to the model (for debugging, often used with `return_all=true`).
  * `conversation`: An optional vector of `AbstractMessage` objects representing the conversation history. If not provided, it is initialized as an empty vector.
  * `http_kwargs`: A named tuple of HTTP keyword arguments.
  * `api_kwargs`: A named tuple of API keyword arguments.
  * `kwargs`: Prompt variables to be used to fill the prompt/template

# Returns

If `return_all=false` (default):

  * `msg`: An `AIMessage` object representing the generated AI message, including the content, status, tokens, and elapsed time.

Use `msg.content` to access the extracted string.

If `return_all=true`:

  * `conversation`: A vector of `AbstractMessage` objects representing the full conversation history, including the response from the AI model (`AIMessage`).

See also: `ai_str`, `aai_str`, `aigenerate`, `aiembed`, `aiclassify`, `aiextract`, `aitemplates`

# Notes

  * All examples below use model "gpt4v", which is an alias for model ID "gpt-4-vision-preview"
  * `max_tokens` in the `api_kwargs` is preset to 2500, otherwise OpenAI enforces a default of only a few hundred tokens (~300). If your output is truncated, increase this value

# Example

Describe the provided image:

```julia
msg = aiscan("Describe the image"; image_path="julia.png", model="gpt4v")
# [ Info: Tokens: 1141 @ Cost: $0.0117 in 2.2 seconds
# AIMessage("The image shows a logo consisting of the word "julia" written in lowercase")
```

You can provide multiple images at once as a vector and ask for "low" level of detail (cheaper):

```julia
msg = aiscan("Describe the image"; image_path=["julia.png","python.png"], image_detail="low", model="gpt4v")
```

You can use this function as a nice and quick OCR (transcribe text in the image) with a template `:OCRTask`.  Let's transcribe some SQL code from a screenshot (no more re-typing!):

```julia
# Screenshot of some SQL code
image_url = "https://www.sqlservercentral.com/wp-content/uploads/legacy/8755f69180b7ac7ee76a69ae68ec36872a116ad4/24622.png"
msg = aiscan(:OCRTask; image_url, model="gpt4v", task="Transcribe the SQL code in the image.", api_kwargs=(; max_tokens=2500))

# [ Info: Tokens: 362 @ Cost: $0.0045 in 2.5 seconds
# AIMessage("```sql
# update Orders <continue>

# You can add syntax highlighting of the outputs via Markdown
using Markdown
msg.content |> Markdown.parse
```

Notice that we enforce `max_tokens = 2500`. That's because OpenAI seems to default to ~300 tokens, which provides incomplete outputs. Hence, we set this value to 2500 as a default. If you still get truncated outputs, increase this value.

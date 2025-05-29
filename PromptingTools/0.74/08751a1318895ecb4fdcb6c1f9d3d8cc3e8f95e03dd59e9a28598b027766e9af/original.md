```
aiimage(prompt_schema::AbstractOpenAISchema, prompt::ALLOWED_PROMPT_TYPE;
    image_size::AbstractString = "1024x1024",
    image_quality::AbstractString = "standard",
    image_n::Integer = 1,
    verbose::Bool = true,
    api_key::String = OPENAI_API_KEY,
    model::String = MODEL_IMAGE_GENERATION,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    http_kwargs::NamedTuple = (retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), api_kwargs::NamedTuple = NamedTuple(),
    kwargs...)
```

Generates an image from the provided `prompt`. If multiple "messages" are provided in `prompt`, it extracts the text ONLY from the last message!

Image (or the reference to it) will be returned in a `DataMessage.content`, the format will depend on the `api_kwargs.response_format` you set.

Can be used for generating images of varying quality and style with `dall-e-*` models. This function DOES NOT SUPPORT multi-turn conversations (ie, do not provide previous conversation via `conversation` argument).

# Arguments

  * `prompt_schema`: An optional object to specify which prompt template should be applied (Default to `PROMPT_SCHEMA = OpenAISchema`)
  * `prompt`: Can be a string representing the prompt for the AI conversation, a `UserMessage`, a vector of `AbstractMessage` or an `AITemplate`
  * `image_size`: String-based resolution of the image, eg, "1024x1024". Only some resolutions are supported - see the [API docs](https://platform.openai.com/docs/api-reference/images/create).
  * `image_quality`: It can be either "standard" or "hd". Defaults to "standard".
  * `image_n`: The number of images to generate. Currently, only single image generation is allowed (`image_n = 1`).
  * `verbose`: A boolean indicating whether to print additional information.
  * `api_key`: A string representing the API key for accessing the OpenAI API.
  * `model`: A string representing the model to use for generating the response. Can be an alias corresponding to a model ID defined in `MODEL_IMAGE_GENERATION`.
  * `return_all::Bool=false`: If `true`, returns the entire conversation history, otherwise returns only the last message (the `AIMessage`).
  * `dry_run::Bool=false`: If `true`, skips sending the messages to the model (for debugging, often used with `return_all=true`).
  * `conversation`: An optional vector of `AbstractMessage` objects representing the conversation history. Currently, NOT ALLOWED.
  * `http_kwargs`: A named tuple of HTTP keyword arguments.
  * `api_kwargs`: A named tuple of API keyword arguments. Several important arguments are highlighted below:

      * `response_format`: The format image should be returned in. Can be one of "url" or "b64_json". Defaults to "url" (the link will be inactived in 60 minutes).
      * `style`: The style of generated images (DALL-E 3 only). Can be either "vidid" or "natural". Defauls to "vidid".
  * `kwargs`: Prompt variables to be used to fill the prompt/template

# Returns

If `return_all=false` (default):

  * `msg`: A `DataMessage` object representing one or more generated images, including the rewritten prompt if relevant, status, and elapsed time.

Use `msg.content` to access the extracted string.

If `return_all=true`:

  * `conversation`: A vector of `AbstractMessage` objects representing the full conversation history, including the response from the AI model (`AIMessage`).

See also: `ai_str`, `aai_str`, `aigenerate`, `aiembed`, `aiclassify`, `aiextract`, `aiscan`, `aitemplates`

# Notes

  * This function DOES NOT SUPPORT multi-turn conversations (ie, do not provide previous conversation via `conversation` argument).
  * There is no token tracking provided by the API, so the messages will NOT report any cost despite costing you money!
  * You MUST download any URL-based images within 60 minutes. The links will become inactive.

# Example

Generate an image:

```julia
# You can experiment with `image_size`, `image_quality` kwargs!
msg = aiimage("A white cat on a car")

# Download the image into a file
using Downloads
Downloads.download(msg.content[:url], "cat_on_car.png")

# You can also see the revised prompt that DALL-E 3 used
msg.content[:revised_prompt]
# Output: "Visualize a pristine white cat gracefully perched atop a shiny car. 
# The cat's fur is stark white and its eyes bright with curiosity. 
# As for the car, it could be a contemporary sedan, glossy and in a vibrant color. 
# The scene could be set under the blue sky, enhancing the contrast between the white cat, the colorful car, and the bright blue sky."
```

Note that you MUST download any URL-based images within 60 minutes. The links will become inactive.

If you wanted to download image directly into the DataMessage, provide `response_format="b64_json"` in `api_kwargs`:

```julia
msg = aiimage("A white cat on a car"; image_quality="hd", api_kwargs=(; response_format="b64_json"))

# Then you need to use Base64 package to decode it and save it to a file:
using Base64
write("cat_on_car_hd.png", base64decode(msg.content[:b64_json]));
```

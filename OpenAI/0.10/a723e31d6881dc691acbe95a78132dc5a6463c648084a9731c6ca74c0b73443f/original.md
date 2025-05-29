Create completion

# Arguments:

  * `api_key::String`: OpenAI API key
  * `model_id::String`: Model id

# Keyword Arguments (check the OpenAI docs for the exhaustive list):

  * `temperature::Float64=1.0`: What sampling temperature to use, between 0 and 2. Higher values like 0.8 will make the output more random, while lower values like 0.2 will make it more focused and deterministic. We generally recommend altering this or top_p but not both.
  * `top_p::Float64=1.0`: An alternative to sampling with temperature, called nucleus sampling, where the model considers the results of the tokens with top_p probability mass. So 0.1 means only the tokens comprising the top 10% probability mass are considered. We generally recommend altering this or temperature but not both.

For more details about the endpoint and additional arguments, visit [https://platform.openai.com/docs/api-reference/completions](https://platform.openai.com/docs/api-reference/completions)

# HTTP.request keyword arguments:

  * `http_kwargs::NamedTuple=NamedTuple()`: Keyword arguments to pass to HTTP.request (e. g., `http_kwargs=(connection_timeout=2,)` to set a connection timeout of 2 seconds).

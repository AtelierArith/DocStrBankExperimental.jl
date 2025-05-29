Create images

# Arguments:

  * `api_key::String`: OpenAI API key
  * `prompt`: The input text to generate the image(s) for, as String or array of tokens.
  * `n::Integer`: Optional. The number of images to generate. Must be between 1 and 10.
  * `size::String`: Optional. Defaults to 1024x1024. The size of the generated images. Must be one of 256x256, 512x512, or 1024x1024.

# Keyword Arguments:

  * `http_kwargs::NamedTuple`: Optional. Keyword arguments to pass to HTTP.request.
  * `response_format::String`: Optional. Defaults to "url". The format of the response. Must be one of "url" or "b64_json".

For additional details about the endpoint, visit [https://platform.openai.com/docs/api-reference/images/create](https://platform.openai.com/docs/api-reference/images/create)

# once the request is made,

download like this: `download(r.response["data"][begin]["url"], "image.png")`

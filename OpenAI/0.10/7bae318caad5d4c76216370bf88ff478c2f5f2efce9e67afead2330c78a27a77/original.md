Create chat

# Arguments:

  * `api_key::String`: OpenAI API key
  * `model_id::String`: Model id
  * `messages::Vector`: The chat history so far.
  * `streamcallback=nothing`: Function to call on each chunk (delta) of the chat response in streaming mode.

# Keyword Arguments (check the OpenAI docs for the exhaustive list):

  * `temperature::Float64=1.0`: What sampling temperature to use, between 0 and 2. Higher values like 0.8 will make the output more random, while lower values like 0.2 will make it more focused and deterministic. We generally recommend altering this or top_p but not both.
  * `top_p::Float64=1.0`: An alternative to sampling with temperature, called nucleus sampling, where the model considers the results of the tokens with top_p probability mass. So 0.1 means only the tokens comprising the top 10% probability mass are considered. We generally recommend altering this or temperature but not both.

!!! note
    Do not use `stream=true` option here, instead use the `streamcallback` keyword argument (see the relevant section below).


For more details about the endpoint and additional arguments, visit [https://platform.openai.com/docs/api-reference/chat](https://platform.openai.com/docs/api-reference/chat)

# HTTP.request keyword arguments:

  * `http_kwargs::NamedTuple=NamedTuple()`: Keyword arguments to pass to HTTP.request (e. g., `http_kwargs=(connection_timeout=2,)` to set a connection timeout of 2 seconds).

## Example:

```julia
julia> CC = create_chat("..........", "gpt-4o-mini", 
    [Dict("role" => "user", "content"=> "What is the OpenAI mission?")]
);

julia> CC.response.choices[1][:message][:content]
"

The OpenAI mission is to create safe and beneficial artificial intelligence (AI) that can help humanity achieve its full potential. The organization aims to discover and develop technical approaches to AI that are safe and aligned with human values. OpenAI believes that AI can help to solve some of the world's most pressing problems, such as climate change, disease, inequality, and poverty. The organization is committed to advancing research and development in AI while ensuring that it is used ethically and responsibly."
```

### Streaming

When a function that takes a single `String` as an argument is passed in the `streamcallback` argument, a request will be made in in streaming mode. The `streamcallback` callback will be called on every line of the streamed response. Here we use a callback that prints out the current time to demonstrate how different parts of the response are received at different times. 

The response body will reflect the chunked nature of the response, so some reassembly will be required to recover the full message returned by the API.

```julia
julia> CC = create_chat(key, "gpt-4o-mini",
           [Dict("role" => "user", "content"=> "What continent is New York in? Two word answer.")],
       streamcallback = x->println(Dates.now()));
       2023-03-27T12:34:50.428
2023-03-27T12:34:50.524
2023-03-27T12:34:50.524
2023-03-27T12:34:50.524
2023-03-27T12:34:50.545
2023-03-27T12:34:50.556
2023-03-27T12:34:50.556

julia> map(r->r["choices"][1]["delta"], CC.response)
5-element Vector{JSON3.Object{Base.CodeUnits{UInt8, SubString{String}}, SubArray{UInt64, 1, Vector{UInt64}, Tuple{UnitRange{Int64}}, true}}}:
 {
   "role": "assistant"
}
 {
   "content": "North"
}
 {
   "content": " America"
}
 {
   "content": "."
}
 {}
```

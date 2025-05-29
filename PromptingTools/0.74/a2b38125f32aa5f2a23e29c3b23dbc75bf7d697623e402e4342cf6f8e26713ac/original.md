```
aiembed(prompt_schema::AbstractOpenAISchema,
        doc_or_docs::Union{AbstractString, AbstractVector{<:AbstractString}},
        postprocess::F = identity;
        verbose::Bool = true,
        api_key::String = OPENAI_API_KEY,
        model::String = MODEL_EMBEDDING, 
        http_kwargs::NamedTuple = (retry_non_idempotent = true,
                                   retries = 5,
                                   readtimeout = 120),
        api_kwargs::NamedTuple = NamedTuple(),
        kwargs...) where {F <: Function}
```

The `aiembed` function generates embeddings for the given input using a specified model and returns a message object containing the embeddings, status, token count, and elapsed time.

## Arguments

  * `prompt_schema::AbstractOpenAISchema`: The schema for the prompt.
  * `doc_or_docs::Union{AbstractString, AbstractVector{<:AbstractString}}`: The document or list of documents to generate embeddings for.
  * `postprocess::F`: The post-processing function to apply to each embedding. Defaults to the identity function.
  * `verbose::Bool`: A flag indicating whether to print verbose information. Defaults to `true`.
  * `api_key::String`: The API key to use for the OpenAI API. Defaults to `OPENAI_API_KEY`.
  * `model::String`: The model to use for generating embeddings. Defaults to `MODEL_EMBEDDING`.
  * `http_kwargs::NamedTuple`: Additional keyword arguments for the HTTP request. Defaults to `(retry_non_idempotent = true, retries = 5, readtimeout = 120)`.
  * `api_kwargs::NamedTuple`: Additional keyword arguments for the OpenAI API. Defaults to an empty `NamedTuple`.
  * `kwargs...`: Additional keyword arguments.

## Returns

  * `msg`: A `DataMessage` object containing the embeddings, status, token count, and elapsed time. Use `msg.content` to access the embeddings.

# Example

```julia
msg = aiembed("Hello World")
msg.content # 1536-element JSON3.Array{Float64...
```

We can embed multiple strings at once and they will be `hcat` into a matrix   (ie, each column corresponds to one string)

```julia
msg = aiembed(["Hello World", "How are you?"])
msg.content # 1536×2 Matrix{Float64}:
```

If you plan to calculate the cosine distance between embeddings, you can normalize them first:

```julia
using LinearAlgebra
msg = aiembed(["embed me", "and me too"], LinearAlgebra.normalize)

# calculate cosine distance between the two normalized embeddings as a simple dot product
msg.content' * msg.content[:, 1] # [1.0, 0.787]
```

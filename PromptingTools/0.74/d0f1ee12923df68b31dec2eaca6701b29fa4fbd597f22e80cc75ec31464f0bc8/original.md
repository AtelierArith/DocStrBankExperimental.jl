```
aiembed(prompt_schema::AbstractOllamaManagedSchema,
        doc_or_docs::Union{AbstractString, AbstractVector{<:AbstractString}},
        postprocess::F = identity;
        verbose::Bool = true,
        api_key::String = "",
        model::String = MODEL_EMBEDDING,
        http_kwargs::NamedTuple = (retry_non_idempotent = true,
                                   retries = 5,
                                   readtimeout = 120),
        api_kwargs::NamedTuple = NamedTuple(),
        kwargs...) where {F <: Function}
```

The `aiembed` function generates embeddings for the given input using a specified model and returns a message object containing the embeddings, status, token count, and elapsed time.

## Arguments

  * `prompt_schema::AbstractOllamaManagedSchema`: The schema for the prompt.
  * `doc_or_docs::Union{AbstractString, AbstractVector{<:AbstractString}}`: The document or list of documents to generate embeddings for. The list of documents is processed sequentially,  so users should consider implementing an async version with with `Threads.@spawn`
  * `postprocess::F`: The post-processing function to apply to each embedding. Defaults to the identity function, but could be `LinearAlgebra.normalize`.
  * `verbose::Bool`: A flag indicating whether to print verbose information. Defaults to `true`.
  * `api_key::String`: The API key to use for the OpenAI API. Defaults to `""`.
  * `model::String`: The model to use for generating embeddings. Defaults to `MODEL_EMBEDDING`.
  * `http_kwargs::NamedTuple`: Additional keyword arguments for the HTTP request. Defaults to empty `NamedTuple`.
  * `api_kwargs::NamedTuple`: Additional keyword arguments for the Ollama API. Defaults to an empty `NamedTuple`.
  * `kwargs`: Prompt variables to be used to fill the prompt/template

## Returns

  * `msg`: A `DataMessage` object containing the embeddings, status, token count, and elapsed time.

Note: Ollama API currently does not return the token count, so it's set to `(0,0)`

# Example

```julia
const PT = PromptingTools
schema = PT.OllamaManagedSchema()

msg = aiembed(schema, "Hello World"; model="openhermes2.5-mistral")
msg.content # 4096-element JSON3.Array{Float64...
```

We can embed multiple strings at once and they will be `hcat` into a matrix   (ie, each column corresponds to one string)

```julia
const PT = PromptingTools
schema = PT.OllamaManagedSchema()

msg = aiembed(schema, ["Hello World", "How are you?"]; model="openhermes2.5-mistral")
msg.content # 4096×2 Matrix{Float64}:
```

If you plan to calculate the cosine distance between embeddings, you can normalize them first:

```julia
const PT = PromptingTools
using LinearAlgebra
schema = PT.OllamaManagedSchema()

msg = aiembed(schema, ["embed me", "and me too"], LinearAlgebra.normalize; model="openhermes2.5-mistral")

# calculate cosine distance between the two normalized embeddings as a simple dot product
msg.content' * msg.content[:, 1] # [1.0, 0.34]
```

Similarly, you can use the `postprocess` argument to materialize the data from JSON3.Object by using `postprocess = copy`

```julia
const PT = PromptingTools
schema = PT.OllamaManagedSchema()

msg = aiembed(schema, "Hello World", copy; model="openhermes2.5-mistral")
msg.content # 4096-element Vector{Float64}
```

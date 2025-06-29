```
aihelp([cfg::RT.AbstractRAGConfig, index::RT.AbstractChunkIndex,]
    question::AbstractString;
    verbose::Integer = 1,
    model = MODEL_CHAT,
    return_all::Bool = false)
```

Generates a response for a given question using a Retrieval-Augmented Generation (RAG) approach over Julia documentation (or any other knowledge pack). 

If you return RAGResult (`return_all=true`), you can use `AIHelpMe.pprint` to pretty-print the result and see the sources/"support" scores for each chunk of the answer.

The answer will depend on the knowledge packs loaded, see `?load_index!`.

You can also use add docstrings from any package you have loaded (or all of them), see `?update_index` and make sure to provide your new updated index explicitly!

# Arguments

  * `cfg::AbstractRAGConfig`: The RAG configuration.
  * `index::AbstractChunkIndex`: The chunk index (contains chunked and embedded documentation).
  * `question::AbstractString`: The question to be answered.
  * `model::String`: A chat/generation model used for generating the final response, default is `MODEL_CHAT`.
  * `return_all::Bool`: If `true`, returns a `RAGResult` (provides details of the pipeline + allows pretty-printing with `pprint(result)`).
  * `search::Union{Nothing, Bool}`: If `true`, uses TavilySearchRefiner to add web search results to the context. See `?PromptingTools.Experimental.RAGTools.TavilySearchRefiner` for details.
  * `rerank::Union{Nothing, Bool}`: If `true`, uses CohereReranker to rerank the chunks. See `?PromptingTools.Experimental.RAGTools.CohereReranker` for details.

# Returns

  * If `return_all` is `false`, returns the generated message (`msg`).
  * If `return_all` is `true`, returns a `RAGResult` (provides details of the pipeline + allows pretty-printing with `pprint(result)`)

# Notes

  * Function always saves the last context in global `LAST_RESULT` for inspection of sources/context regardless of `return_all` value.

# Examples

Using `aihelp` to get a response for a question:

```julia
using AIHelpMe: build_index

index = build_index(...)  # create an index that contains Makie.jl documentation (or any loaded package that you have)

question = "How to make a barplot in Makie.jl?"
msg = aihelp(index, question)
```

If you want a pretty-printed answer with highlighted sources, you can use the `return_all` argument and `pprint` utility:

```julia
using AIHelpMe: pprint

result = aihelp(index, question; return_all = true)
pprint(result)
```

If you loaded a knowledge pack, you do not have to provide the index.

```julia
# Load Makie knowledge pack
AIHelpMe.load_index!(:makie)

question = "How to make a barplot in Makie.jl?"
msg = aihelp(question)
```

If you know it's a hard question, you can use the `search` and `rerank` arguments to add web search results to the context and rerank the chunks.

```julia
using AIHelpMe: pprint

question = "How to make a barplot in Makie.jl?"
result = aihelp(question; search = true, rerank = true, return_all = true)
pprint(result) # nicer display with sources for each chunk/sentences (look for square brackets)
```

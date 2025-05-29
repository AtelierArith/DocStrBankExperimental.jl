```
setpropertynested(nt::NamedTuple, parent_keys::Vector{Symbol},
	key::Symbol,
	value
```

)

Setter for a property `key` in a nested NamedTuple `nt`, where the property is nested to a key in `parent_keys`.

Useful for nested kwargs where we want to change some property in `parent_keys` subset (eg, `model` in `retriever_kwargs`).

# Examples

```julia
kw = (; abc = (; def = "x"))
setpropertynested(kw, [:abc], :def, "y")
# Output: (abc = (def = "y",),)
```

Practical example of changing all `model` keys in CHAT-based steps in the pipeline:

```julia
# changes :model to "gpt4t" whenever the parent key is in the below list (chat-based steps)
setpropertynested(kwargs,
	[:rephraser_kwargs, :tagger_kwargs, :answerer_kwargs, :refiner_kwargs],
	:model, "gpt4t")
```

Or changing an embedding model (across both indexer and retriever steps, because it's same step name):

```julia
kwargs = setpropertynested(
		kwargs, [:embedder_kwargs],
		:model, "text-embedding-3-large"
	)
```

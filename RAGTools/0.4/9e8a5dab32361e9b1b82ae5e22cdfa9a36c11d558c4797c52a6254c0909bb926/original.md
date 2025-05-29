```
getpropertynested(
	nt::NamedTuple, parent_keys::Vector{Symbol}, key::Symbol, default = nothing)
```

Get a property `key` from a nested NamedTuple `nt`, where the property is nested to a key in `parent_keys`.

Useful for nested kwargs where we want to get some property in `parent_keys` subset (eg, `model` in `retriever_kwargs`).

# Examples

```julia
kw = (; abc = (; def = "x"))
getpropertynested(kw, [:abc], :def)
# Output: "x"
```

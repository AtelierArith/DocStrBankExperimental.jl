```julia
layers(con::AbstractContext) -> ::Vector{Pair{Int64, String}}
```

Shows layers of a `Context`.

```example
using Gattino

example = hist(["hello"], [500])

layers(example)
```

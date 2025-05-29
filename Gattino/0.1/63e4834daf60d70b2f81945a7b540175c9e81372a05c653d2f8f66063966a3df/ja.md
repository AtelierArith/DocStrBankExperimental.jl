```julia
layers(con::AbstractContext) -> ::Vector{Pair{Int64, String}}
```

`Context`のレイヤーを表示します。

```example
using Gattino

example = hist(["hello"], [500])

layers(example)
```

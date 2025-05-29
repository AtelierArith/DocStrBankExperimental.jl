```
digraphtype{G<:AGraphOrDiGraph}(::Type{G})
```

`G`に対応する有向グラフの型。`G<:ADiGraph`の場合は`G`を返し、`G<:AGraph`の場合は型`H<:ADiGraph`を返します。

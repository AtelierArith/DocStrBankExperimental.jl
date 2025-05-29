```
graphtype{G<:AGraphOrDiGraph}(::Type{G})
```

`G`に対応するグラフタイプ。`G<:AGraph`の場合は`G`を返し、`G<:ADiGraph`の場合はタイプ`H<:AGraph`を返します。

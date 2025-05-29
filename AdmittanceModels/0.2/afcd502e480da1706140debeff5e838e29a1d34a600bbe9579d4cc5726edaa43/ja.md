```
PSOModel(circuit::Circuit, port_edges::Vector{<:Tuple},
    port_names::AbstractVector)
```

与えられたエッジ上のポートを持つ回路のためのPSOModelを作成します。最初の頂点が接地として選ばれ、他のすべての頂点が接地の隣接点であるスパニングツリーが使用されます。

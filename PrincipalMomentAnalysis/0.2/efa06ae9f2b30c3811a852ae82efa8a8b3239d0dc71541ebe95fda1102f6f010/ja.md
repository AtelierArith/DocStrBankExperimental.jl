```
SimplexGraph{T<:AbstractMatrix{Bool}, S<:Union{Number,AbstractVector{<:Number}}}
```

1:Nから番号が付けられた単体の集合を記述する構造体。オプションで、各単体に重みを割り当てることができます。

## 使用法

```
SimplexGraph(G, w=true)
```

SimplexGraphを構築します。`G`はブール値の`MxN`行列で、`M`は頂点の数、`N`は単体の数です。`G`の各列は1つの単体を表します。真は頂点が単体の一部であることを意味し、偽はそうでないことを意味します。オプションで、長さNのベクトル`w`を使用して各単体の重み（総質量）を指定できます。重みのデフォルトは1（真）です。

`pma`、`groupsimplices`、`timeseriessimplices`、`neighborsimplices`も参照してください。

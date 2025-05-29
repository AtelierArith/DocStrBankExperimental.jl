```
nearby_positions(pos, model::ABM{<:DiscreteSpace}, r=1; kwargs...)
```

指定された`position`の「半径」`r`内のすべての位置のイテラブルを返します（指定された`position`は除外されます）。`position`は`model`の空間構造と型が一致する必要があります。

`r`の値と可能なキーワードは[`nearby_ids`](@ref)と同様に動作します。

この関数は、有限の位置を持つ離散空間にのみ存在します。

```
nearby_positions(position, model::ABM{<:OpenStreetMapSpace}; kwargs...) → positions
```

[`OpenStreetMapSpace`](@ref)の場合、これは「近くの交差点」を意味し、OSMの基盤となるグラフ上で直接動作し、指定された位置に最も近い交差点ノードを提供します。 ```

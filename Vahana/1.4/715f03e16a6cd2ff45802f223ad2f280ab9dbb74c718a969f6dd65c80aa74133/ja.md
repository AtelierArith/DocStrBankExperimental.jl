```
connect_raster_neighbors!(sim, name::Symbol, edge_constructor; [distance::Int, metric:: Symbol, periodic::Bool])
```

すべてのセルは、互いに最大 `distance` の距離にある場合（`metric` を使用）にエッジで接続され、エッジは `edge_constructor` で作成されます。

`edge_constructor` は、型 Tuple{CartesianIndex, CartesianIndex} の引数を1つ持つ関数でなければなりません。最初の CartesianIndex はソースノードの位置であり、2番目の CartesianIndex はターゲットノードの位置です。

有効なメトリックは :chebyshev, :euclidean および :manhatten です。

キーワード periodic は、すべての次元が周期的であるかどうかを決定します（例えば、2次元の場合、ラスタはトーラスです）。

オプションのキーワード引数のデフォルト値は、`distance` に対して 1、`metric` に対して :chebyshev、`periodic` に対して true です。これはムーア近傍に相当します。:manhatten メトリックは、フォン・ノイマン近傍のセルを接続するために使用できます。

`agent_constructor` によって作成されたエージェントのエージェントタイプは、すでに [`register_agenttype!`](@ref) を介して登録されている必要があります。

詳細は [`add_raster!`](@ref) を参照してください。

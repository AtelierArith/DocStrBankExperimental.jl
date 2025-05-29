```
FullGridCellList(; min_corner, max_corner, search_radius = 0.0,
                 periodicity = false, backend = DynamicVectorOfVectors{Int32},
                 max_points_per_cell = 100)
```

各（空または非空の）セルが点のリストに割り当てられる長方形（軸に沿った）領域の単純なセルリスト実装です。このセルリストは、すべての点が常に指定された領域内にある場合にのみ機能します。

`min_corner` と `max_corner` のみを設定し、他の引数にはデフォルト値を使用して、空の「テンプレート」セルリストを作成します。これは空の「テンプレート」近傍検索を作成するために使用できます。詳細については [`copy_neighborhood_search`](@ref) を参照してください。

# キーワード

  * `min_corner`: 負の座標方向における領域のコーナーの座標。
  * `max_corner`: 正の座標方向における領域のコーナーの座標。
  * `search_radius = 0.0`: 近傍検索の検索半径で、セルのサイズを決定します。テンプレートを作成するにはデフォルトの `0.0` を使用します（上記参照）。
  * `periodicity = false`: 近傍検索で [`PeriodicBox`](@ref) を使用する場合は `true` に設定します。 [`copy_neighborhood_search`](@ref) を使用する場合、このオプションは無視でき、自動的に近傍検索の周期性に応じて設定されます。
  * `backend = DynamicVectorOfVectors{Int32}`: 実際のセルリストを格納するデータ構造のタイプ。次のいずれかです。

      * `Vector{Vector{Int32}}`: 散発的なメモリですが、非常にメモリ効率が良いです。
      * `DynamicVectorOfVectors{Int32}`: 連続したメモリで、キャッシュヒットを最適化します。
  * `max_points_per_cell = 100`: セルあたりの最大点数。この値は `DynamicVectorOfVectors` を割り当てるために使用されます。 `Vector{Vector{Int32}}` バックエンドでは使用されません。

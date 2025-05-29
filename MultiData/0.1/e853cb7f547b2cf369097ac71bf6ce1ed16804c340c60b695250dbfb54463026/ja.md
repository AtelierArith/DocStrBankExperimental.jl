```
`MultiDataset(df, grouped_variables)`
```

`AbstractDataFrame` `df` から `MultiDataset` を作成し、`grouped_variables` に基づいてそのモダリティを初期化します。

`grouped_variables` は、選択された変数のインデックスを表す整数の `AbstractVector` の変数グルーピングの `AbstractVector` です。

モダリティと変数の順序は重要です。

```julia-repl
julia> df = DataFrame(
                  :age => [30, 9],
                  :name => ["Python", "Julia"],
                  :stat1 => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]],
                  :stat2 => [[cos(i) for i in 1:50000], [sin(i) for i in 1:50000]]
              )
2×4 DataFrame
 Row │ age    name    stat1                              stat2                             ⋯
     │ Int64  String  Array…                             Array…                            ⋯
─────┼──────────────────────────────────────────────────────────────────────────────────────
   1 │    30  Python  [0.841471, 0.909297, 0.14112, -0…  [0.540302, -0.416147, -0.989992,… ⋯
   2 │     9  Julia   [0.540302, -0.416147, -0.989992,…  [0.841471, 0.909297, 0.14112, -0…

julia> md = MultiDataset([[2]], df)
● MultiDataset
   └─ dimensionalities: (0,)
- Modality 1 / 1
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Spare variables
   └─ dimensionality: mixed
2×3 SubDataFrame
 Row │ age    stat1                              stat2
     │ Int64  Array…                             Array…
─────┼─────────────────────────────────────────────────────────────────────────────
   1 │    30  [0.841471, 0.909297, 0.14112, -0…  [0.540302, -0.416147, -0.989992,…
   2 │     9  [0.540302, -0.416147, -0.989992,…  [0.841471, 0.909297, 0.14112, -0…
```

```
`MultiDataset(df; group = :none)`
```

`AbstractDataFrame` `df` から `MultiDataset` を作成し、モダリティを自動的に選択します。

モダリティの選択は、`group` 引数によって制御され、次のように設定できます。

  * `:none` (デフォルト): モダリティは作成されません
  * `:all`: すべての変数がその [`dimensionality`](@ref) によってグループ化されます
  * グループ化される次元のリスト。

注意: `:all` と `:none` は `group` に受け入れられる唯一の `Symbol` です。

# TODO: 整数のベクターを `group` に渡す修正

# TODO: 例を再記述

# 例

```julia-repl
julia> df = DataFrame(
                  :age => [30, 9],
                  :name => ["Python", "Julia"],
                  :stat1 => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]],
                  :stat2 => [[cos(i) for i in 1:50000], [sin(i) for i in 1:50000]]
              )
2×4 DataFrame
 Row │ age    name    stat1                              stat2                             ⋯
     │ Int64  String  Array…                             Array…                            ⋯
─────┼──────────────────────────────────────────────────────────────────────────────────────
   1 │    30  Python  [0.841471, 0.909297, 0.14112, -0…  [0.540302, -0.416147, -0.989992,… ⋯
   2 │     9  Julia   [0.540302, -0.416147, -0.989992,…  [0.841471, 0.909297, 0.14112, -0…

julia> md = MultiDataset(df)
● MultiDataset
   └─ dimensionalities: ()
- Spare variables
   └─ dimensionality: mixed
2×4 SubDataFrame
 Row │ age    name    stat1                              stat2                             ⋯
     │ Int64  String  Array…                             Array…                            ⋯
─────┼──────────────────────────────────────────────────────────────────────────────────────
   1 │    30  Python  [0.841471, 0.909297, 0.14112, -0…  [0.540302, -0.416147, -0.989992,… ⋯
   2 │     9  Julia   [0.540302, -0.416147, -0.989992,…  [0.841471, 0.909297, 0.14112, -0…


julia> md = MultiDataset(df; group = :all)
● MultiDataset
   └─ dimensionalities: (0, 1)
- Modality 1 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ age    name
     │ Int64  String
─────┼───────────────
   1 │    30  Python
   2 │     9  Julia
- Modality 2 / 2
   └─ dimensionality: 1
2×2 SubDataFrame
 Row │ stat1                              stat2
     │ Array…                             Array…
─────┼──────────────────────────────────────────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…  [0.540302, -0.416147, -0.989992,…
   2 │ [0.540302, -0.416147, -0.989992,…  [0.841471, 0.909297, 0.14112, -0…


julia> md = MultiDataset(df; group = [0])
● MultiDataset
   └─ dimensionalities: (0, 1, 1)
- Modality 1 / 3
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ age    name
     │ Int64  String
─────┼───────────────
   1 │    30  Python
   2 │     9  Julia
- Modality 2 / 3
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…
- Modality 3 / 3
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat2
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.540302, -0.416147, -0.989992,…
   2 │ [0.841471, 0.909297, 0.14112, -0…
```

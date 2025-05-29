```
loaddataset(datasetpath; onlywithlabels = [], shufflelabels = [], rng = Random.GLOBAL_RNG)
```

`Labels.csv` の存在に基づいて、Dataset から `MultiDataset` または `LabeledMultiDataset` を作成します。

# 引数

  * `datasetpath` は Dataset の位置を示す `AbstractString` です。
  * `onlywithlabels` は `AbstractVector{AbstractVector{Pair{AbstractString,AbstractVector{Any}}}}` で、ラベルとその値を指定することによって、どの部分の Dataset をロードするかを選択するために使用されます。中央から始めて、各 `Pair{AbstractString,AbstractVector{Any}}` は、`AbstractString` としてラベルの名前を含み、`AbstractVector{Any}` としてそのラベルの値を含む必要があります。1 つのベクトル内の各 Pair は異なるラベルを参照する必要があるため、Dataset に合計 n のラベルがある場合、この Pair のベクトルには最大 n 要素を含めることができます。これは、要素が互いに組み合わさるためです。各 Pair のベクトルはフィルターとして機能します。同じラベルは異なる Pair のベクトルで使用できますが、それらは互いに組み合わさることはありません。`onlywithlabels` が空のベクトル（デフォルト）である場合、関数は Dataset 全体をロードします。
  * `shufflelabels` はシャッフルするラベルの名前の `AbstractVector` です（デフォルト = []、シャッフルなしを意味します）。
  * `rng` はシャッフル時に使用される乱数生成器です（再現性のため）。整数（`MersenneTwister` のシードとして使用）または `AbstractRNG` であることができます。

# 例

```julia-repl
julia> df_data = DataFrame(
           :id => [1, 2, 3, 4, 5],
           :age => [30, 9, 30, 40, 9],
           :name => ["Python", "Julia", "C", "Java", "R"],
           :stat => [deepcopy(ts_sin), deepcopy(ts_cos), deepcopy(ts_sin), deepcopy(ts_cos), deepcopy(ts_sin)]
       )
5×4 DataFrame
 Row │ id     age    name    stat
     │ Int64  Int64  String  Array…
─────┼─────────────────────────────────────────────────────────
   1 │     1     30  Python  [0.841471, 0.909297, 0.14112, -0…
   2 │     2      9  Julia   [0.540302, -0.416147, -0.989992,…
   3 │     3     30  C       [0.841471, 0.909297, 0.14112, -0…
   4 │     4     40  Java    [0.540302, -0.416147, -0.989992,…
   5 │     5      9  R       [0.841471, 0.909297, 0.14112, -0…

julia> lmd = LabeledMultiDataset(
    MultiDataset([[4]], deepcopy(df_data)),
    [2,3],
)
● LabeledMultiDataset
   ├─ labels
   │   ├─ age: Set([9, 30, 40])
   │   └─ name: Set(["C", "Julia", "Python", "Java", "R"])
   └─ dimensionalities: (1,)
- Modality 1 / 1
   └─ dimensionality: 1
5×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…
   3 │ [0.841471, 0.909297, 0.14112, -0…
   4 │ [0.540302, -0.416147, -0.989992,…
   5 │ [0.841471, 0.909297, 0.14112, -0…
- Spare variables
   └─ dimensionality: 0
5×1 SubDataFrame
 Row │ id
     │ Int64
─────┼───────
   1 │     1
   2 │     2
   3 │     3
   4 │     4
   5 │     5

julia> savedataset("langs", lmd, force = true)

julia> loaddataset("langs", onlywithlabels = [ ["name" => ["Julia"], "age" => ["9"]] ] )
Instances count: 1
Total size: 981670 bytes
● LabeledMultiDataset
   ├─ labels
   │   ├─ age: Set(["9"])
   │   └─ name: Set(["Julia"])
   └─ dimensionalities: (1,)
- Modality 1 / 1
   └─ dimensionality: 1
1×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.540302, -0.416147, -0.989992,…
- Spare variables
   └─ dimensionality: 0
1×1 SubDataFrame
 Row │ id
     │ Int64
─────┼───────
   1 │     2

julia> loaddataset("langs", onlywithlabels = [ ["name" => ["Julia"], "age" => ["30"]] ] )
Instances count: 0
Total size: 0 bytes
ERROR: AssertionError: No instance found

julia> loaddataset("langs", onlywithlabels = [ ["name" => ["Julia"]] , ["age" => ["9"]] ] )
Instances count: 2
Total size: 1963537 bytes
● LabeledMultiDataset
   ├─ labels
   │   ├─ age: Set(["9"])
   │   └─ name: Set(["Julia", "R"])
   └─ dimensionalities: (1,)
- Modality 1 / 1
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.540302, -0.416147, -0.989992,…
   2 │ [0.841471, 0.909297, 0.14112, -0…
- Spare variables
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ id
     │ Int64
─────┼───────
   1 │     2
   2 │     5

julia> loaddataset("langs", onlywithlabels = [ ["name" => ["Julia"]], ["name" => ["C"], "age" => ["30"]] ] )
Instances count: 2
Total size: 1963537 bytes
● LabeledMultiDataset
    ├─ labels
    │   ├─ age: Set(["9", "30"])
    │   └─ name: Set(["C", "Julia"])
    └─ dimensionalities: (1,)
- Modality 1 / 1
    └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.540302, -0.416147, -0.989992,…
   2 │ [0.841471, 0.909297, 0.14112, -0…
- Spare variables
    └─ dimensionality: 0
2×1 SubDataFrame
 Row │ id
     │ Int64
─────┼───────
   1 │     2
   2 │     3
```

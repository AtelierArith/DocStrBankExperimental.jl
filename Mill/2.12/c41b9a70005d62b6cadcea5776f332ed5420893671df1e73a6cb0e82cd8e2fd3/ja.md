```
reflectinmodel(x::AbstractMillNode, fm=d -> Dense(d, 10), fa=BagCount ∘ SegmentedMeanMax;
    fsm=Dict(), fsa=Dict(), single_key_identity=true, single_scalar_identity=true, all_imputing=false)
```

[`Mill.jl`](https://github.com/CTUAvastLab/Mill.jl) モデルを構築して `x` を処理できるようにします。

すべての内部 `Dense` レイヤーは、入力次元 `d` を受け取り、適切なモデルを返す関数 `fm` を使用して構築されます。すべての集約演算子は、同様に `fa` を使用して構築されます。

`fsm` および `fsa` キーワード引数を使用することで、より細かい制御が可能です。これらは `c => f` ペアの `Dict` であり、`c` は [`HierarchicalUtils.jl`](@ref) からの `String` トラバーサルコードで、`f` は関数です。これらの定義は `fm` と `fa` を上書きします。

単一の子（サブツリー）を持つ [`ProductNode`](@ref) に遭遇した場合、その最終的な `m` モデルは `fm` や `fsm` を使用するのではなく `identity` としてインスタンス化されます。これは `single_key_identity` で制御できます。

同様に、[`ArrayNode`](@ref) がデータ `X` を含み、`size(X, 1)` が `1` の場合、対応するモデルは `single_scalar_identity` が `false` でない限り `identity` としてインスタンス化されます。

デフォルトでは、`reflectinmodel` は葉の最初の `Dense` レイヤーを、データ型が欠損データが存在することを示唆する場合にのみインプットします。これは以下のタイプに適用されます。

  * `Array`,
  * `SparseMatrixCSC` または `SparseVector`,
  * `PooledArray`,
  * [`MaybeHotVector`](@ref),
  * [`MaybeHotMatrix`](@ref), および
  * [`NGramMatrix`](@ref)

`eltype` が `{Union{Missing, T}} where T` のタイプです。`all_imputing` が `true` の場合、これらのタイプのすべての葉 `Dense` レイヤーはそのインプットバリアントに置き換えられます。

# 例

```jldoctest
julia> n1 = ProductNode(a=ArrayNode(NGramMatrix(["a", missing])))
ProductNode  2 obs
  ╰── a: ArrayNode(2053×2 NGramMatrix with Union{Missing, Int64} elements)  2 obs

julia> n2 = ProductNode((ArrayNode([0 1]), BagNode(ArrayNode([0 1; 2 3]), bags([1:1, 2:2]))))
ProductNode  2 obs
  ├── ArrayNode(1×2 Array with Int64 elements)  2 obs
  ╰── BagNode  2 obs
        ╰── ArrayNode(2×2 Array with Int64 elements)  2 obs

julia> n = ProductNode((n1, n2))
ProductNode  2 obs
  ├── ProductNode  2 obs
  │     ╰── a: ArrayNode(2053×2 NGramMatrix with Union{Missing, Int64} elements)  2 obs
  ╰── ProductNode  2 obs
        ├── ArrayNode(1×2 Array with Int64 elements)  2 obs
        ╰── BagNode  2 obs
              ╰── ArrayNode(2×2 Array with Int64 elements)  2 obs

julia> reflectinmodel(n)
ProductModel ↦ Dense(20 => 10)  2 arrays, 210 params, 928 bytes
  ├── ProductModel ↦ identity
  │     ╰── a: ArrayModel([postimputing]Dense(2053 => 10))  3 arrays, 20_550 params, 80.398 KiB
  ╰── ProductModel ↦ Dense(11 => 10)  2 arrays, 120 params, 568 bytes
        ├── ArrayModel(identity)
        ╰── BagModel ↦ BagCount([SegmentedMean(10); SegmentedMax(10)]) ↦ Dense(21 => 10)  4 arrays, 240 params, 1.102 KiB
              ╰── ArrayModel(Dense(2 => 10))  2 arrays, 30 params, 208 bytes

julia> reflectinmodel(n, d -> Dense(d, 3), SegmentedMean, all_imputing=true)
ProductModel ↦ Dense(6 => 3)  2 arrays, 21 params, 172 bytes
  ├── ProductModel ↦ identity
  │     ╰── a: ArrayModel([postimputing]Dense(2053 => 3))  3 arrays, 6_165 params, 24.207 KiB
  ╰── ProductModel ↦ Dense(4 => 3)  2 arrays, 15 params, 148 bytes
        ├── ArrayModel([preimputing]Dense(1 => 1))  3 arrays, 3 params, 140 bytes
        ╰── BagModel ↦ SegmentedMean(3) ↦ Dense(3 => 3)  3 arrays, 15 params, 188 bytes
              ╰── ArrayModel([preimputing]Dense(2 => 3))  3 arrays, 11 params, 172 bytes

julia> printtree(n; trav=true)
ProductNode [""]  2 obs
  ├── ProductNode ["E"]  2 obs
  │     ╰── a: ArrayNode(2053×2 NGramMatrix with Union{Missing, Int64} elements) ["M"]  2 obs
  ╰── ProductNode ["U"]  2 obs
        ├── ArrayNode(1×2 Array with Int64 elements) ["Y"]  2 obs
        ╰── BagNode ["c"]  2 obs
              ╰── ArrayNode(2×2 Array with Int64 elements) ["e"]  2 obs

julia> reflectinmodel(n, d -> Dense(d, 3), SegmentedMean;
                        fsm=Dict("e" => d -> Chain(Dense(d, 2), Dense(2, 2))),
                        fsa=Dict("c" => SegmentedLSE),
                        single_key_identity=false,
                        single_scalar_identity=false)
ProductModel ↦ Dense(6 => 3)  2 arrays, 21 params, 172 bytes
  ├── ProductModel ↦ Dense(3 => 3)  2 arrays, 12 params, 136 bytes
  │     ╰── a: ArrayModel([postimputing]Dense(2053 => 3))  3 arrays, 6_165 params, 24.207 KiB
  ╰── ProductModel ↦ Dense(6 => 3)  2 arrays, 21 params, 172 bytes
        ├── ArrayModel(Dense(1 => 3))  2 arrays, 6 params, 112 bytes
        ╰── BagModel ↦ SegmentedLSE(2) ↦ Dense(2 => 3)  4 arrays, 13 params, 220 bytes
              ╰── ArrayModel(Chain(Dense(2 => 2), Dense(2 => 2)))  4 arrays, 12 params, 224 bytes
```

参照: [`AbstractMillNode`](@ref), [`AbstractMillModel`](@ref), [`ProductNode`](@ref), [`BagNode`](@ref), [`ArrayNode`](@ref)。

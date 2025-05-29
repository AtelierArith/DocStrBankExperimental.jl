```
function quanticscrossinterpolate(
    ::Type{ValueType},
    f,
    grid::QuanticsGrids.Grid{n},
    initialpivots::Union{Nothing,AbstractVector{<:AbstractVector}}=nothing;
    nrandominitpivot=5,
    kwargs...
) where {ValueType}
```

関数 $f(\mathbf{x})$ を量子テンソル列として補間します。テンソル列自体は、[`TensorCrossInterpolation.crossinterpolate2`](https://tensor4all.github.io/TensorCrossInterpolation.jl/dev/documentation/#TensorCrossInterpolation.crossinterpolate2-Union{Tuple{N},%20Tuple{ValueType},%20Tuple{Type{ValueType},%20Any,%20Union{Tuple{Vararg{Int64,%20N}},%20Vector{Int64}}},%20Tuple{Type{ValueType},%20Any,%20Union{Tuple{Vararg{Int64,%20N}},%20Vector{Int64}},%20Vector{Vector{Int64}}}}%20where%20{ValueType,%20N}) に実装された2サイトテンソル交差補間アルゴリズムを使用して構築されます。

引数:

  * `ValueType` は `f` の戻り値の型です。自動推論はエラーが発生しやすいです。
  * `f` は補間される関数です。`f` は複数の引数を取ることができます。戻り値の型は `ValueType` である必要があります。
  * `grid` は、バイナリ数字でインデックス付けされた離散点のd次元グリッドを記述する [`QuanticsGrids.jl`](https://github.com/tensor4all/QuanticsGrids.jl) の `Grid{n}` オブジェクトです。グリッドを明示的に構築するのを避けるために、他のオーバーロードのいずれかを使用してください。
  * `initialpivots` は初期化に使用されるピボットのベクトルです。
  * `nrandominitpivot` は、初期ピボットが指定されていない場合に初期化に使用されるランダムピボットの数を決定します。

他のすべての引数は `crossinterpolate2` に転送されます。最も重要な点は:

  * `tolerance::Float64` は補間のための目標許容誤差を指定する浮動小数点数です。デフォルト: `1e-8`。
  * `pivottolerance::Float64` は新しいピボットを追加するための許容誤差を指定する浮動小数点数です。すなわち、テンソル列の結合の切り捨てです。これは許容誤差以下である必要があります。そうでない場合、収束が不可能になることがあります。デフォルト: `tolerance`。
  * `maxbonddim::Int` はTCIの最大結合次元を指定します。デフォルト: `typemax(Int)`、すなわち実質的に無制限です。
  * `maxiter::Int` はTCI構築を中止する前の最大反復回数（すなわち最適化スイープ）です。デフォルト: `200`。

他のすべての引数については、[`TensorCrossInterpolation.crossinterpolate2`](https://tensor4all.github.io/TensorCrossInterpolation.jl/dev/documentation/#TensorCrossInterpolation.crossinterpolate2-Union{Tuple{N},%20Tuple{ValueType},%20Tuple{Type{ValueType},%20Any,%20Union{Tuple{Vararg{Int64,%20N}},%20Vector{Int64}}},%20Tuple{Type{ValueType},%20Any,%20Union{Tuple{Vararg{Int64,%20N}},%20Vector{Int64}},%20Vector{Vector{Int64}}}}%20where%20{ValueType,%20N}) のドキュメントを参照してください。

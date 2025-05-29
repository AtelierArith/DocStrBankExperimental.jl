```
dhg_load(
    fname::AbstractString;
    format::Abstract_HG_format = HGF_Format(),
    HType::Type{H} = DirectedHypergraph,
    T::Type{U} = Bool,
    D::Type{<:AbstractDict{Int, U}} = Dict{Int, T},
    V = Nothing,
    E = Nothing
) where {U <: Real, H <: AbstractDirectedHypergraph}
```

ファイル `fname` からハイパーグラフを読み込みます。デフォルトの保存形式は `hgf` です。

**引数**

  * `HType`: データを保存するハイパーグラフの型
  * `T` : ハイパーグラフの隣接行列に保存される重み値の型
  * `D` : 値を保存するための辞書、デフォルトは `Dict{Int, T}`
  * `V` : ハイパーグラフの頂点に保存される値の型
  * `E` : ハイパーグラフの辺に保存される値の型

```
dhg_load(
    io::IO,
    T::Type{H},
    format::JSON_Format;
    T::Type{U} = Bool,
    D::Type{<:AbstractDict{Int, U}} = Dict{Int,U},
    V = Nothing,
    E = Nothing
) where {H <: AbstractDirectedHypergraph, U <: Real}
```

ストリーム `io` から `json` 形式でハイパーグラフを読み込みます。

**引数**

  * `T` : ハイパーグラフの隣接行列に格納される重み値の型
  * `D` : 値を格納するための辞書、デフォルトは `Dict{Int, T}`
  * `V` : ハイパーグラフの頂点に格納される値の型
  * `E` : ハイパーグラフの辺に格納される値の型

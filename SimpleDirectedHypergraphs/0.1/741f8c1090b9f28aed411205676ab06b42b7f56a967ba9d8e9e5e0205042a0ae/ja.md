```
dhg_load(
    io::IO,
    format::EHGF_Format;
    HType::Type{H} = DirectedHypergraph,
    T::Type{U} = Bool,
    D::Type{<:AbstractDict{Int, U}} = Dict{Int, T},
) where {U <: Real, H <: AbstractDirectedHypergraph}
```

ストリーム `io` から `ehgf` 形式のハイパーグラフを読み込みます。

**引数**

  * `T` : ハイパーグラフの隣接行列に格納される重み値の型
  * `D` : 値を格納するための辞書、デフォルトは `Dict{Int, T}`

最初のコメントを1つスキップします。

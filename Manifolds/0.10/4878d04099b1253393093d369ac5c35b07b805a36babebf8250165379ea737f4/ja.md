```
convert(::Type{ProjectorPoint}, p::AbstractMatrix)
```

点 `p` を [`Stiefel`](@ref) 上の点として、また [`Grassmann`](@ref) 上の点（すなわち部分空間）を表すものとして、該当する部分空間の射影器表現に変換します。すなわち、次のために [`canonical_project!`](@ref) を計算します。

$$
  π^{\mathrm{SG}}(p) = pp^{\mathrm{T}}.
$$

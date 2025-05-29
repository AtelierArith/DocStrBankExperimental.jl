```
convert(::Type{ProjectorPoint}, ::Stiefelpoint)
```

[`Stiefel`](@ref) 上の点 `p` を、[`Grassmann`](@ref) 上の点（すなわち部分空間）を表す点として、該当する部分空間の射影器表現に変換します。すなわち、次の式のために [`canonical_project!`](@ref) を計算します。

$$
  π^{\mathrm{SG}}(p) = pp^{\mathrm{T}}.
$$

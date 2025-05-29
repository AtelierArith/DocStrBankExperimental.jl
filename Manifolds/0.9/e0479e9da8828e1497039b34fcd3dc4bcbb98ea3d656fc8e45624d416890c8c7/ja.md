```
convert(::Type{ProjectorPoint}, ::Stiefelpoint)
```

[`Stiefel`](@ref) 上の点 `p` を、同時に [`Grassmann`](@ref) 上の点（すなわち部分空間）を表すものとして、該当する部分空間の射影器表現に変換します。すなわち、次の [`canonical_project!`](@ref) を計算します。

$$
  π^{\mathrm{SG}}(p) = pp^{\mathrm{T}}.
$$

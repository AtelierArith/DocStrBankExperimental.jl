```
inv(G::AbstractLieGroup, g)
inv!(G::AbstractLieGroup, h, g)
```

群要素 $g^{-1}$ の逆を、[`AbstractGroupOperation`](@ref) $∘$ に関して、[`AbstractLieGroup`](@ref) $\mathcal G$ 上で計算します。すなわち、$h=g^{-1}$ という一意の要素を返します。これは $h∘g=\mathrm{e}$ となるもので、ここで $\mathrm{e}$ は [`Identity`](@ref) を示します。

これは `h` に対してインプレースで行うことができ、副作用なしに、すなわち `inv!(G, g, g)` を実行することができます。

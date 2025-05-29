```
exp∂exp(Z::QuatVec)
```

`Z`の成分に関する`exp(Z)`の値と勾配を返します。

勾配の成分についての詳細は[`∂exp`](@ref)を参照してください。

# 例

```julia
julia> e, ∂e = exp∂exp(randn(QuatVecF64));

```

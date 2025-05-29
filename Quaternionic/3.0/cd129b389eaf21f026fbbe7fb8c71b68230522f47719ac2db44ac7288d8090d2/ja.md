```
log∂log(Z::Rotor)
```

`Z`の成分に関する`log(Z)`の値と勾配を返します。

勾配の成分についての詳細は[`∂log`](@ref)を参照してください。

# 例

```julia
julia> l, ∂l = log∂log(randn(RotorF64));

```

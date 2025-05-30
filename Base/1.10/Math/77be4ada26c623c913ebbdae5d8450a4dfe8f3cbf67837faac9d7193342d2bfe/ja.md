```
exp(x)
```

`x`の自然基底指数を計算します。言い換えれば、$ℯ^x$です。

関連項目としては、[`exp2`](@ref)、[`exp10`](@ref)、および[`cis`](@ref)があります。

# 例

```jldoctest
julia> exp(1.0)
2.718281828459045

julia> exp(im * pi) ≈ cis(pi)
true
```

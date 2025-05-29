```
digamma_reg(z)
```

Digamma function $ψ(z)$ regularised at negative integers thanks to the formula

$$
ψ(1-z) - ψ(z) = π \operatorname{cot}(πz)
$$

# Examples

```jldoctest
julia> digamma_reg(-1)
0.4227843350984672
```

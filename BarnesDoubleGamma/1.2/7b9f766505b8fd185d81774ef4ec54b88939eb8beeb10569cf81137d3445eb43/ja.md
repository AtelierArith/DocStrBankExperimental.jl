```
digamma_reg(z)
```

負の整数で正則化されたディガンマ関数 $ψ(z)$ は、次の式によって与えられます。

$$
ψ(1-z) - ψ(z) = π \operatorname{cot}(πz)
$$

# 例

```jldoctest
julia> digamma_reg(-1)
0.4227843350984672
```

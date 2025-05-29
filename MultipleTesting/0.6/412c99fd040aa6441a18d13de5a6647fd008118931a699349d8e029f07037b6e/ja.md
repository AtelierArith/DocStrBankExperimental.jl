Oracle π₀

# 例

```jldoctest
julia> pvals = PValues([0.001, 0.002, 0.01, 0.03, 0.5]);

julia> estimate(pvals, Oracle(0.5)) # ちょっと退屈...
0.5
```

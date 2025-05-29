最小傾斜 (LSL) π₀ 推定量

# 例

```jldoctest
julia> pvals = PValues([0.001, 0.002, 0.01, 0.03, 0.5]);

julia> estimate(pvals, LeastSlope())
1.0
```

# 参考文献

Benjamini, Y., and Hochberg, Y. (2000). On the Adaptive Control of the False Discovery Rate in Multiple Testing With Independent Statistics. Journal of Educational and Behavioral Statistics 25, 60–83.

Forward-Stop 調整

# 例

```jldoctest
julia> pvals = PValues([0.001, 0.01, 0.03, 0.5]);

julia> adjust(pvals, ForwardStop())
4-element Array{Float64,1}:
 0.0010005003335835344
 0.005525418093542492
 0.013836681223931188
 0.1836643060579347

julia> adjust(pvals, 6, ForwardStop())
4-element Array{Float64,1}:
 0.0010005003335835344
 0.005525418093542492
 0.013836681223931188
 0.1836643060579347
```

# 参考文献

G’Sell, M.G., Wager, S., Chouldechova, A., and Tibshirani, R. (2016). Sequential selection procedures and false discovery rate control. J. R. Stat. Soc. B 78, 423–444.

```
complement(x::Logistic) :: Logistic
```

補完を計算します。すなわち、引数と1の差を計算します。

# 例

```jldoctest
julia> complement(logisticate(0.2))
Logistic{Float64}(1.3862943611198906) ≈ 0.8

julia> 1 - logisticate(0.2)
0.8
```

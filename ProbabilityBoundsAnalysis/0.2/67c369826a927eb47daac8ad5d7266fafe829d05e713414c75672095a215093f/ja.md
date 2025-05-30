```
beta(α :: Interval, β :: Interval)
```

ベータ形状のpbox。パラメータは実数または区間であることができます。

# 例

```jldoctest
julia> a = beta(2,interval(3,4))
Pbox: 	  ~ beta ( range=[0.0, 1.0], mean=[0.33333, 0.4], var=[0.031746, 0.04])
```

参照: [`KN`](@ref), [`meanMinMax`](@ref), [`plot`](@ref)

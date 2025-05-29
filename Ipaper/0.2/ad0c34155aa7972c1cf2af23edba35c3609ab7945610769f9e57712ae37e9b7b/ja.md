```
par_mapslices(f, A::AbstractArray{<:Real,N}, args...; dims=N, kw...)
```

# 引数

  * `dims`: fを適用する次元

@seealso `mapslices`

# 例

```julia
using Ipaper
using Distributions

A = rand(100, 100, 30, 4)
obj_size(A)

par_mapslices(mean, A)

# @time r = mapslices(slope_mk, A; dims=3);
# @time r_par = par_mapslices(slope_mk, A; dims=3); # 5倍速い
```

# TODO: par_mapslicesは効率が低い

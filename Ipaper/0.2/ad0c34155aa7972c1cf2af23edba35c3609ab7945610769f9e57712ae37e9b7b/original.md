```
par_mapslices(f, A::AbstractArray{<:Real,N}, args...; dims=N, kw...)
```

# Arguments

  * `dims`: the dimension apply f

@seealso `mapslices`

# Example

```julia
using Ipaper
using Distributions

A = rand(100, 100, 30, 4)
obj_size(A)

par_mapslices(mean, A)

# @time r = mapslices(slope_mk, A; dims=3);
# @time r_par = par_mapslices(slope_mk, A; dims=3); # 5X faster
```

# TODO: par_mapslices is low efficiency

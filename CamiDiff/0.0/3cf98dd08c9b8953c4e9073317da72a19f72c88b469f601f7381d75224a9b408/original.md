```
castGrid(ID::Int, N::Int, T::Type; h=1, rmax=10, p=5, polynom=[0,1], epn=5, k=5, msg=false)
castGrid(name::String, N::Int, T::Type; h=1, rmax=10, p=5, polynom=[0,1], epn=5, k=5, msg=false)
```

Method to create a [`Grid`](@ref) object that covers the radial range [0, rmax] with `N` points.

`ID = 1`: exponential, `ID = 2`: truncated-exponential, `ID = 3`: linear (uniform) `ID = 4`: polynomial

#### Examples:

```
julia> grid = castGrid(1, 1000, Float64; h = 0.005, rmax = 10, msg=true);
Grid: exponential, Float64, rmax = 10.0, N = 1000, h = 0.005, r0 = 0.0681789

julia> grid = castGrid("exponential", 1000, Float64; h = 0.005, rmax = 10, msg=true);
Grid: exponential, Float64, rmax = 10.0, N = 1000, h = 0.005, r0 = 0.0681789

julia> grid = castGrid(2, 1000, Float64; h = 0.005, rmax = 10, p=5, msg=true);
Grid: truncated-exponential, Float64, rmax = 10.0, N = 1000, p = 5, h = 0.005, r0 = 0.111

julia> grid = castGrid(3, 1000, Float64; h = 0.1, rmax = 10, msg=true);
Grid: linear (uniform), Float64, rmax = 10.0, N = 1000, p = 1, h = 0.1, r0 = 0.1001

julia> grid = castGrid(4, 1000, Float64; h = 0.1, rmax = 10, polynom=[0,0,1], msg=true);
Grid: polynomial of degree 2, Float64, rmax = 10.0, N = 1000, polynom = [0.0, 0.0, 1.0], h = 0.1, r0 = 0.001002

julia> r = grid.r[1:4]; println("r = ", r)
r = [0.0, 1.002003004005006e-5, 4.008012016020024e-5, 9.018027036045053e-5]

julia> r = grid.r[997:1000]; println("r = ", r)
r = [9.9400301202103, 9.96000004008012, 9.979990000010021, 10.0] # note the end of the range (r = rmax) 

julia> r′= grid.r′[1:4]; println("r′ = ", r′)
r′ = [0.0, 2.0040060080100123e-5, 4.008012016020025e-5, 6.012018024030035e-5]

julia> r′′= grid.r′′[1:4]; println("r′′ = ", r′′)
r′′ = [2.004006008010012e-5, 2.004006008010012e-5, 2.004006008010012e-5, 2.004006008010012e-5]
```

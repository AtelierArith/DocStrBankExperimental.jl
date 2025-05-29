```
minimize(m, f, x0 = zeros(length(x0));
               lowerbound = -ones(length(x0)),
               upperbound = ones(length(x0)),
               max_iterations = 10^4,
               min_mesh_size = eps(Float64)/2,
               constraints = [],
               verbosity = Silent)
```

Minimize function `f` with method `m`. For possible methods `m` see [`LtMADS`](@ref), [`OrthoMADS`](@ref), [`MADS`](@ref), [`RobustLtMADS`](@ref), [`RobustOrthoMADS`](@ref), [`RobustMADS`](@ref). Constraints can be defined by boolean functions, e.g. `constraints = [x -> sum(x) > 1, x -> x[1]^2 < 3]`. Possible `verbosity`-levels are `Silent` or `Progress`.

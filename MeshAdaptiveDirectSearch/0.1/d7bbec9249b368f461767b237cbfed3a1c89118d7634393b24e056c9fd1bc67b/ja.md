```
minimize(m, f, x0 = zeros(length(x0));
               lowerbound = -ones(length(x0)),
               upperbound = ones(length(x0)),
               max_iterations = 10^4,
               min_mesh_size = eps(Float64)/2,
               constraints = [],
               verbosity = Silent)
```

関数 `f` を方法 `m` で最小化します。可能な方法 `m` については [`LtMADS`](@ref), [`OrthoMADS`](@ref), [`MADS`](@ref), [`RobustLtMADS`](@ref), [`RobustOrthoMADS`](@ref), [`RobustMADS`](@ref) を参照してください。制約はブール関数によって定義できます。例えば、`constraints = [x -> sum(x) > 1, x -> x[1]^2 < 3]` のように指定します。可能な `verbosity` レベルは `Silent` または `Progress` です。

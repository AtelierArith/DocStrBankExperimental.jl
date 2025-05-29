```
splitarg(arg)
```

Match function arguments (whether from a definition or a function call) such as `x::Int=2` and return `(arg_name, arg_type, is_splat, default)`. `arg_name` and `default` are `nothing` when they are absent. For example:

```julia
julia> map(splitarg, (:(f(a=2, x::Int=nothing, y, args...))).args[2:end])
4-element Array{Tuple{Symbol,Symbol,Bool,Any},1}:
 (:a, :Any, false, 2)
 (:x, :Int, false, :nothing)
 (:y, :Any, false, nothing)
 (:args, :Any, true, nothing)
```

See also: [`combinearg`](@ref)

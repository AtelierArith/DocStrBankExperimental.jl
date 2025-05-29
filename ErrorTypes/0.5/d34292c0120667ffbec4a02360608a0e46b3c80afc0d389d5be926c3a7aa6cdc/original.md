```
Ok{T}
```

The success state of a `Result{T, E}`, carrying an object of type `T`. For convenience, `Ok(x)` creates a dummy value that can be converted to the appropriate `Result type`.

Instances of `Ok` and its mirror image `Err` cannot be directly constructed.

See also: [`Err`](@ref)

```jldoctest
julia> function reciprocal(x::Int)::Result{Float64, String}
           iszero(x) && return Err("Division by zero")
           Ok(1 / x)
       end;

julia> reciprocal(4)
Result{Float64, String}(Ok(0.25))

julia> reciprocal(0)
Result{Float64, String}(Err("Division by zero"))
```

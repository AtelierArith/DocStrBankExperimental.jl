```
@unwrap_or(expr, exec)
```

Evaluate `expr` to a `Result`. If `expr` is a error value, evaluate `exec` and return that. Else, return the wrapped value in `expr`.

See also: [`@unwrap_error_or`](@ref)

# Examples

```julia
julia> safe_inv(x)::Option{Float64} = iszero(x) ? none : Ok(1/x);

julia> function skip_inv_sum(it)
    sum = 0.0
    for i in it
        sum += @unwrap_or safe_inv(i) continue
    end
    sum
end;

julia> skip_inv_sum([2,1,0,1,2])
3.0
```

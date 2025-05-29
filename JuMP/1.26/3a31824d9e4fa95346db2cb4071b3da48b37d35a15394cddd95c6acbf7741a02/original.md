```
op_string(mime::MIME, x::GenericNonlinearExpr, ::Val{op}) where {op}
```

Return the string that should be printed for the operator `op` when [`function_string`](@ref) is called with `mime` and `x`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2], Bin);

julia> f = @expression(model, x[1] || x[2]);

julia> op_string(MIME("text/plain"), f, Val(:||))
"||"
```

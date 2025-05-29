```
function_string(
    mode::MIME,
    func::Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}},
)
```

Return a `String` representing the function `func` using print mode `mode`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> function_string(MIME("text/plain"), 2 * x + 1)
"2 x + 1"
```

```
impute(data::T, imp; kwargs...) -> T
```

Returns a new copy of the `data` with the missing data imputed by the imputor `imp`. For matrices and tables, data is imputed one variable/column at a time. If this is not the desired behaviour then you should overload this method or specify a different `dims` value.

# Arguments

  * `data`: the data to be impute
  * `imp::Imputor`: the Imputor method to use

# Returns

  * the input `data` with values imputed

# Example

```jldoctest
julia> using Impute: Interpolate, impute

julia> v = [1.0, 2.0, missing, missing, 5.0]
5-element Vector{Union{Missing, Float64}}:
 1.0
 2.0
  missing
  missing
 5.0

julia> impute(v, Interpolate())
5-element Vector{Union{Missing, Float64}}:
 1.0
 2.0
 3.0
 4.0
 5.0
```

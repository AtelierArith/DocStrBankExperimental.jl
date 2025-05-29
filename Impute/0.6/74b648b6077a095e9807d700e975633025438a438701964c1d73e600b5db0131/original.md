```
impute!(data::A, imp; dims=:, kwargs...) -> A
```

Impute the `missing` values in the array `data` using the imputor `imp`. Optionally, you can specify the dimension to impute along.

# Arguments

  * `data::AbstractArray{Union{T, Missing}}`: the data to be impute along dimensions `dims`
  * `imp::Imputor`: the Imputor method to use

# Keyword Arguments

  * `dims=:`: The dimension to impute along. `:rows` and `:cols` are also supported for matrices.

# Returns

  * `AbstractArray{Union{T, Missing}}`: the input `data` with values imputed

# NOTES

1. Matrices have a deprecated `dims=2` special case as `dims=:` is a breaking change
2. Mutation isn't guaranteed for all array types, hence we return the result
3. `eachslice` is used internally which requires Julia 1.1

# Example

```jldoctest
julia> using Impute: Interpolate, impute!

julia> M = [1.0 2.0 missing missing 5.0; 1.1 2.2 3.3 missing 5.5]
2×5 Matrix{Union{Missing, Float64}}:
 1.0  2.0   missing  missing  5.0
 1.1  2.2  3.3       missing  5.5

julia> impute!(M, Interpolate(); dims=1)
2×5 Matrix{Union{Missing, Float64}}:
 1.0  2.0  3.0  4.0  5.0
 1.1  2.2  3.3  4.4  5.5

julia> M
2×5 Matrix{Union{Missing, Float64}}:
 1.0  2.0  3.0  4.0  5.0
 1.1  2.2  3.3  4.4  5.5
```

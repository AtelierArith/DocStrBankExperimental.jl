```
create_ols_approximation(y::Vector{<:Real}, x::Vector{<:Real}, base_x::Real = 0.0, degree::Integer = 1, intercept::Bool = true)
create_ols_approximation(y::Vector{<:Real}, x::Union{Vector{DateTime},Vector{Date},Vector{Union{Date,DateTime}}}, base_x::Union{Date,DateTime} = global_base_date, degree::Integer = 1, intercept::Bool = true)
```

An approximation function calculated via OLS.

### Inputs

  * `y` - A `Vector` with the y coordinates
  * `x` - A `Vector` with the x coordinates
  * `base_x` - A real that offsets the x. So a coordinate with x value of 2.0 will be converted to 1.8 if base_x is 0.2.
  * `degree` - What the highest power of x should be. So if this is 3 then the equation will have x, x^2, x^3 as predictors.
  * `intercept` - Should there be an x intercept.

### Returns

  * A `Sum_Of_Functions` containing the approximation function.

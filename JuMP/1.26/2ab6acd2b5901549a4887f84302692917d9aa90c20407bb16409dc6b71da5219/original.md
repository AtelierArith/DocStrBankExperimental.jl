```
lp_matrix_data(model::GenericModel{T})
```

Given a JuMP model of a linear program, return an [`LPMatrixData{T}`](@ref) struct storing data for an equivalent linear program in the form:

$$
\begin{aligned}
\min & c^\top x + c_0 \\
      & b_l \le A x \le b_u \\
      & x_l \le x \le x_u
\end{aligned}
$$

where elements in `x` may be continuous, integer, or binary variables.

## Fields

The struct returned by [`lp_matrix_data`](@ref) has the fields:

  * `A::SparseArrays.SparseMatrixCSC{T,Int}`: the constraint matrix in sparse matrix form.
  * `b_lower::Vector{T}`: the dense vector of row lower bounds. If missing, the value of `typemin(T)` is used.
  * `b_upper::Vector{T}`: the dense vector of row upper bounds. If missing, the value of `typemax(T)` is used.
  * `x_lower::Vector{T}`: the dense vector of variable lower bounds. If missing, the value of `typemin(T)` is used.
  * `x_upper::Vector{T}`: the dense vector of variable upper bounds. If missing, the value of `typemax(T)` is used.
  * `c::Vector{T}`: the dense vector of linear objective coefficients
  * `c_offset::T`: the constant term in the objective function.
  * `sense::MOI.OptimizationSense`: the objective sense of the model.
  * `integers::Vector{Int}`: the sorted list of column indices that are integer variables.
  * `binaries::Vector{Int}`: the sorted list of column indices that are binary variables.
  * `variables::Vector{GenericVariableRef{T}}`: a vector of [`GenericVariableRef`](@ref), corresponding to order of the columns in the matrix form.
  * `affine_constraints::Vector{ConstraintRef}`: a vector of [`ConstraintRef`](@ref), corresponding to the order of rows in the matrix form.

## Limitations

The models supported by [`lp_matrix_data`](@ref) are intentionally limited to linear programs.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2] >= 0);

julia> @constraint(model, x[1] + 2 * x[2] <= 1);

julia> @objective(model, Max, x[2]);

julia> data = lp_matrix_data(model);

julia> data.A
1×2 SparseArrays.SparseMatrixCSC{Float64, Int64} with 2 stored entries:
 1.0  2.0

julia> data.b_lower
1-element Vector{Float64}:
 -Inf

julia> data.b_upper
1-element Vector{Float64}:
 1.0

julia> data.x_lower
2-element Vector{Float64}:
 0.0
 0.0

julia> data.x_upper
2-element Vector{Float64}:
 Inf
 Inf

julia> data.c
2-element Vector{Float64}:
 0.0
 1.0

julia> data.c_offset
0.0

julia> data.sense
MAX_SENSE::OptimizationSense = 1
```

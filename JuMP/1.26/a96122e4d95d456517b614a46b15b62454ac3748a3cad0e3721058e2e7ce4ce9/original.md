```
is_solved_and_feasible(
    model::GenericModel;
    allow_local::Bool = true,
    allow_almost::Bool = false,
    dual::Bool = false,
    result::Int = 1,
)
```

Return `true` if:

  * the [`termination_status`](@ref) is one of:

      * [`OPTIMAL`](@ref) (the solver found a global optimum)
      * [`LOCALLY_SOLVED`](@ref) (the solver found a local optimum, which may also be the global optimum, but the solver could not prove so).
  * the [`primal_status`](@ref) of the result index `result` is `FEASIBLE_POINT`.

This function is conservative, in that it returns `false` for situations like the solver terminating with a feasible solution due to a time limit.

If this function returns `false`, use [`termination_status`](@ref), [`result_count`](@ref), [`primal_status`](@ref) and [`dual_status`](@ref) to understand what solutions are available (if any).

See also: [`assert_is_solved_and_feasible`](@ref).

## Keyword arguments

### `allow_local`

If `allow_local = false`, then this function returns `true` only if the [`termination_status`](@ref) is [`OPTIMAL`](@ref).

### `allow_almost`

If `allow_almost = true`, then the [`termination_status`](@ref) may additionally be [`ALMOST_OPTIMAL`](@ref) or [`ALMOST_LOCALLY_SOLVED`](@ref) (if `allow_local`), and the [`primal_status`](@ref) and [`dual_status`](@ref) may additionally be [`NEARLY_FEASIBLE_POINT`](@ref).

### `dual`

If `dual`, additionally check that an optimal dual solution is available via [`dual_status`](@ref). The `allow_` keywords control both the primal and dual solutions.

### `result`

The index of the result to query. This value is passed to the `result` keyword arguments of [`primal_status`](@ref) and [`dual_status`](@ref).

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> is_solved_and_feasible(model)
false

julia> is_solved_and_feasible(
           model;
           allow_almost = true,
           dual = true,
           result = 2,
       )
false
```

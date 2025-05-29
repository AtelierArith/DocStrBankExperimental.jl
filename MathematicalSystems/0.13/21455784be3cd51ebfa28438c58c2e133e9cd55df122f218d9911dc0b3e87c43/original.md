```
ivp(expr...)
```

Return an instance of the initial-value problem type corresponding to the given expressions.

### Input

  * `expr` – expressions separated by commas which define the dynamic equation,           the constraint sets or the dimensionality of the system, and the set           of initial states (required)

### Output

An initial-value problem that best matches the given expressions.

### Notes

This macro behaves like the `@system` macro, the sole difference being that in `@ivp` the constraint on the set of initial states is mandatory. For the technical details we refer to the documentation of [`@system`](@ref).

The macro can also be called with a `system` argument of type `AbstractSystem` in the form `@ivp(system, state(0) ∈ initial_set)`.

### Examples

```jldoctest ivp_macro
julia> p = @ivp(x' = -x, x(0) ∈ [1.0]);

julia> typeof(p)
InitialValueProblem{LinearContinuousSystem{Float64, IdentityMultiple{Float64}}, Vector{Float64}}

julia> initial_state(p)
1-element Vector{Float64}:
 1.0

julia> sys = @system(x' = [1 0; 0 1] * x);

julia> @ivp(sys, x(0) ∈ [-1, 1])
InitialValueProblem{LinearContinuousSystem{Int64, Matrix{Int64}}, Vector{Int64}}(LinearContinuousSystem{Int64, Matrix{Int64}}([1 0; 0 1]), [-1, 1])
```

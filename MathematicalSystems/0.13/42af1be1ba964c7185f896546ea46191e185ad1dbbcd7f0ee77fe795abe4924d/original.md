```
InitialValueProblem{S <: AbstractSystem, XT} <: AbstractSystem
```

Parametric composite type for initial value problems. It is parameterized in the system's type and the initial state's type

### Fields

  * `s`  – system
  * `x0` – initial state

### Examples

The linear system $x' = -x$ with initial condition $x₀ = [-1/2, 1/2]$:

```jldoctest
julia> s = LinearContinuousSystem([-1.0 0.0; 0.0 -1.0]);

julia> x₀ = [-1/2, 1/2];

julia> p = InitialValueProblem(s, x₀);

julia> initial_state(p) # same as p.x0
2-element Vector{Float64}:
 -0.5
  0.5

julia> statedim(p)
2

julia> inputdim(p)
0
```

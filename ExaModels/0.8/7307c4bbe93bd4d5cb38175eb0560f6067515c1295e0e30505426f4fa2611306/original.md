```
constraint(core, generator; start = 0, lcon = 0,  ucon = 0)
```

Adds constraints specified by a `generator` to `core`, and returns an `Constraint` object.

## Keyword Arguments

  * `start`: The initial guess of the solution. Can either be `Number`, `AbstractArray`, or `Generator`.
  * `lcon` : The constraint lower bound. Can either be `Number`, `AbstractArray`, or `Generator`.
  * `ucon` : The constraint upper bound. Can either be `Number`, `AbstractArray`, or `Generator`.

## Example

```jldoctest
julia> using ExaModels

julia> c = ExaCore();

julia> x = variable(c, 10);

julia> constraint(c, x[i] + x[i+1] for i=1:9; lcon = -1, ucon = (1+i for i=1:9))
Constraint

  s.t. (...)
       g♭ ≤ [g(x,p)]_{p ∈ P} ≤ g♯

  where |P| = 9
```

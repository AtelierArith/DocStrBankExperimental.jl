```
objective(core::ExaCore, generator)
```

Adds objective terms specified by a `generator` to `core`, and returns an `Objective` object. Note: it is assumed that the terms are summed.

## Example

```jldoctest
julia> using ExaModels

julia> c = ExaCore();

julia> x = variable(c, 10);

julia> objective(c, x[i]^2 for i=1:10)
Objective

  min (...) + ∑_{p ∈ P} f(x,p)

  where |P| = 10
```

```
constraint!(c::C, c1, gen::Base.Generator) where {C<:ExaCore}
```

Expands the existing constraint `c1` in `c` by adding additional constraint terms specified by a `generator`.

# Arguments

  * `c::C`: The model to which the constraints are added.
  * `c1`: An initial constraint value or expression.
  * `gen::Base.Generator`: A generator that produces the pair of constraint index and term to be added.

## Example

```jldoctest
julia> using ExaModels

julia> c = ExaCore();

julia> x = variable(c, 10);

julia> c1 = constraint(c, x[i] + x[i+1] for i=1:9; lcon = -1, ucon = (1+i for i=1:9));

julia> constraint!(c, c1, i => sin(x[i+1]) for i=4:6)
Constraint Augmentation

  s.t. (...)
       g♭ ≤ (...) + ∑_{p ∈ P} h(x,p) ≤ g♯

  where |P| = 3
```

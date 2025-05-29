```
nid(F::System; options...)
```

Calls [`numerical_irreducible_decomposition`](@ref).

### Example

```julia-repl
julia> @var x, y
julia> f = [x^2 + y^2 - 1]
julia> N = nid(f)

Numerical irreducible decomposition with 1 components
• 1 component(s) of dimension 1.

 degree table of components:
╭───────────┬───────────────────────╮
│ dimension │ degrees of components │
├───────────┼───────────────────────┤
│     1     │           2           │
╰───────────┴───────────────────────╯
```

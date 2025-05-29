```
Composition(partscomps)
Composition(parts, comps)
Composition(part₁=comp₁, part₂=part₂, ...)
Composition(comps)
Composition(comp₁, comp₂, ...)
```

A D-part composition as defined by Aitchison 1986.

## Examples

A 2-part composition with parts `a=0.1` and `b=0.8`:

```julia
julia> Composition(a=0.2, b=0.8)
julia> Composition((a=0.2, b=0.8))
julia> Composition((:a, :b), (0.2, 0.8))
```

When the names of the parts are not specified, the constructor uses default names `w1`, `w2`, ..., `wD`:

```
julia> Composition(0.1, 0.8)
julia> Composition((0.1, 0.8))
```

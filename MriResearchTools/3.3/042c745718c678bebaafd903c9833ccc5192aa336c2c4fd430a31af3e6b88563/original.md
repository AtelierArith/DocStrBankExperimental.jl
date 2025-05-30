```
brain_mask(mask)
```

Tries to extract the brain from a mask with skull and a gap between brain and skull.

# Examples

```julia-repl
julia> mask = robustmask(mag)
julia> brain = brain_mask(mask)
```

See also [`robustmask`](@ref)

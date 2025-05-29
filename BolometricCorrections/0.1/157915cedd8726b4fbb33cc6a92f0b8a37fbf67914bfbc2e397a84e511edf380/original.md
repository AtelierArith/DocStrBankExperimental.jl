```
zeropoints(grid::AbstractBCGrid)
zeropoints(table::AbstractBCTable)
```

Return the correct concrete instance of [`AbstractZeropoints`](@ref BolometricCorrections.AbstractZeropoints) for the type of `grid` or `table`.

```jldoctest
julia> zeropoints(MISTBCGrid("JWST")) isa BolometricCorrections.MIST.MISTZeropoints
true
```

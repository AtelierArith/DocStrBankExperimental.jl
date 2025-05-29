```
chemistry(mix::AbstractBCTable)
chemistry(mix::AbstractBCGrid)
```

Returns the correct concrete instance of `AbstractChemicalMixture` for the provided bolometric correction grid or table. This provides a convenient  programmatic way to obtain this chemical information.

```jldoctest
julia> grid = MISTBCGrid("JWST");

julia> chemistry(grid)
BolometricCorrections.MIST.MISTChemistry()

julia> table = grid(-1.5, 0.03);

julia> chemistry(table)
BolometricCorrections.MIST.MISTChemistry()
```

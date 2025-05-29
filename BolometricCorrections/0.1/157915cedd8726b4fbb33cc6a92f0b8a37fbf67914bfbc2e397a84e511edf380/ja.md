```
zeropoints(grid::AbstractBCGrid)
zeropoints(table::AbstractBCTable)
```

`grid`または`table`の型に対して、[`AbstractZeropoints`](@ref BolometricCorrections.AbstractZeropoints)の正しい具体的インスタンスを返します。

```jldoctest
julia> zeropoints(MISTBCGrid("JWST")) isa BolometricCorrections.MIST.MISTZeropoints
true
```

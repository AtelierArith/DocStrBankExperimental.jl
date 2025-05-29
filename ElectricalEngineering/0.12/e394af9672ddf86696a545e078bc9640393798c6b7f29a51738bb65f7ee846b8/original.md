# Function call

`par(z...)`

# Description

This calculates the parallel connection of impedances. Optionally, the calculation can be performed using units from the module Unitful.

The functions `par` and `∥` are redundant impementations.

# Variables

`z` Vector of impedances

# Examples

```julia
julia> using Unitful,Unitful.DefaultSymbols,ElectricalEngineering
julia> par(4,6)
2.4
julia> par(4Ω,6Ω)
2.4 Ω

```

Type `\Omega` and hit the `tab` key to autocomplete the parallel symbol Ω

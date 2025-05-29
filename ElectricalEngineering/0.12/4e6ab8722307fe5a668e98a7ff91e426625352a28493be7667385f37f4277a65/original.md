# Function call

`∠(phi)`

# Description

Creates a complex quantity with length 1 and angle `phi`

# Variables

`phi` Angle of complex quantity; if module Unitful is utilized, the angle may be specified in degrees, by using unit `°`

# Examples

```julia
julia> using Unitful, Unitful.DefaultSymbols, ElectricalEngineering
julia> U1 = 2V*∠(90°)
-0.0 + 2.0im V
```

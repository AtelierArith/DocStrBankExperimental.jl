# Function call

`printuln(r...; label="")`

# Description

This function prints a real or complex variable in an optionally specified unit

# Variables

`r[1]` Text string to printed, indicating the variable name or description; a maximum of 16 characters is allowed, in case the optional variable `label` is NOT specified; in  case of specifying the variable `label`, the maximum length of `r[1]` may not exceed 12 characters

`r[2]` Variable to be printed; the variable may be real or complex, units assigned from the module Unitful are allowed; vectors of variables are also allowed

`r[3]` Optional target unit of `r[2]` to be displayed

`label` Optional four character label structuring the output of variables, e.g., `label = "(a)"`

# Examples

```julia
julia> using Unitful, Unitful.DefaultSymbols, ElectricalEngineering
julia> U1 = 300V+j*400V
julia> printuln("U1", U1, kV)
              U1 = 0.3 kV + j 0.4 kV
                 = 0.5 kV ∠ 53.1301°
julia> printuln("real(U1)", real(U1), kV)
        real(U1) = 0.3 kV
julia> printuln("U1", U1, V, label="(a)")
(a)           U1 = 300 V + j 400 V
                 = 500 V ∠ 53.1301°
```

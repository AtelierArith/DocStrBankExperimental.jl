```
get_spec(val::AbstractSpec,st::ThermodynamicState)
get_spec(val::Type{AbstractSpec},st::ThermodynamicState)
```

Returns the first specification of the type `val` present in the state `st`. returns `nothing` if not found.

## Example

```julia-repl
julia> a1 = state(n = [1.1,2.2,3.3],T=273.15,mol_h = 101.342)
ThermodynamicState with 3 properties:
  Molar amounts : [1.1, 2.2, 3.3][mol]
  Temperature : 273.15[K]
  Molar enthalpy : 101.342[J mol^-1]

julia> get_spec(Enthalpy,a1)
  spec(mol_h = 101.342[J mol^-1])

julia> get_spec(VolumeAmount,a1) == nothing
  true
```

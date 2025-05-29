```
has_spec(val::AbstractSpec,st::ThermodynamicState)::Bool
has_spec(val::Type{AbstractSpec},st::ThermodynamicState)::Bool
```

は、状態 `st` に存在する型 `val` の仕様を確認します。

## 例

```julia-repl
julia> a1 = state(n = [1.1,2.2,3.3],T=273.15,mol_h = 101.342)
ThermodynamicState with 3 properties:
  Molar amounts : [1.1, 2.2, 3.3][mol]
  Temperature : 273.15[K]
  Molar enthalpy : 101.342[J mol^-1]

julia> has_spec(Enthalpy,a1)
  true

julia> has_spec(VolumeAmount,a1) == nothing
  false
```

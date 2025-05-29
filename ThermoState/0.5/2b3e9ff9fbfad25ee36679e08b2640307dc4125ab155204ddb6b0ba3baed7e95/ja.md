```
get_spec(val::AbstractSpec,st::ThermodynamicState)
get_spec(val::Type{AbstractSpec},st::ThermodynamicState)
```

状態 `st` に存在する型 `val` の最初の仕様を返します。見つからない場合は `nothing` を返します。

## 例

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

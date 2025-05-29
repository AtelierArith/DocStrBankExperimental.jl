SpeciesRxnMapの構造体の配列を作成します。SpeciesRxnMapは、参加反応におけるspecies_idと化学量論係数の複合構造体です。

# 使用法

```
species_rxn_map(gas_species,sm)
```

  * gas_species::Array{String,1} : 気相種のリスト
  * sm::SurfaceMechanism : SurfaceMechanism複合型

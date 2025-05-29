```
Model{L, H[, O]}
```

シミュレーションに使用される主要なコンテナです。型パラメータは次のように指定されます。

  * `L <:`[`AbstractLattice`](@ref)
  * `H <:`[`AbstractHamiltonian`](@ref)
  * `O <:`[`AbstractObservable`](@ref)

      * 観測可能なものが提供されていない場合、[`NullObservable`](@ref) が使用されます。

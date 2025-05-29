```
VPIndex{C,S} <: SymbolicStateIndex{C,S}
idx = VPIndex(comp, sub)
```

頂点のパラメータへのシンボリックインデックス：

  * `comp`: コンポーネントインデックス、intまたはintのコレクション
  * `sub`: サブインデックス、int、シンボル、またはそれらのコレクション

`SymbolicIndexingInterface`をサポートするオブジェクト、例えば[`NWParameter`](@ref)や`ODEProblem`にインデックスを付けるために使用できます。

関連情報: [`EPIndex`](@ref), [`VIndex`](@ref), [`EIndex`](@ref)

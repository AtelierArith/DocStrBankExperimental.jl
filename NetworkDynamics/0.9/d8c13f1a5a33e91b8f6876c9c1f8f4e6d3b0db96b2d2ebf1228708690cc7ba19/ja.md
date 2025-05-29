```
EPIndex{C,S} <: SymbolicStateIndex{C,S}
idx = VEIndex(comp, sub)
```

パラメータの頂点へのシンボリックインデックス：

  * `comp`: コンポーネントインデックス、整数または整数のコレクション
  * `sub`: サブインデックス、整数、シンボル、またはそれらのコレクション

`SymbolicIndexingInterface`をサポートするオブジェクト、例えば[`NWParameter`](@ref)や`ODEProblem`にインデックスを付けるために使用できます。

関連情報: [`VPIndex`](@ref), [`VIndex`](@ref), [`EIndex`](@ref)

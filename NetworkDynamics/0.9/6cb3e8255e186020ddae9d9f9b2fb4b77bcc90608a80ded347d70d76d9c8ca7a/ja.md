```
VIndex{C,S} <: SymbolicStateIndex{C,S}
idx = VIndex(comp, sub)
```

頂点状態変数のためのシンボリックインデックス。

  * `comp`: コンポーネントインデックス、intまたはintのコレクション
  * `sub`: サブインデックス、int、シンボルまたはそれらのコレクション

```
VIndex(1, :P)      # 頂点1、変数:P
VIndex(1:5, 1)     # 頂点1から5までの最初の状態
VIndex(7, (:x,:y)) # 頂点7の状態:xと:y
VIndex(2)          # 2番目の頂点モデルを参照
```

`SymbolicIndexingInterface`をサポートするオブジェクトにインデックスを付けるために使用できます。例えば、[`NWState`](@ref)、[`NWParameter`](@ref)または`ODESolution`。

関連情報: [`EIndex`](@ref)、[`VPIndex`](@ref)、[`EPIndex`](@ref)

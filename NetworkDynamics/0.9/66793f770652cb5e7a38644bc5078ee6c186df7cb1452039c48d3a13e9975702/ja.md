```
EIndex{C,S} <: SymbolicStateIndex{C,S}
idx = EIndex(comp, sub)
```

エッジ状態変数のためのシンボリックインデックス。

  * `comp`: コンポーネントインデックス、整数または整数のコレクション
  * `sub`: サブインデックス、整数、シンボル、またはそれらのコレクション

```
EIndex(1, :P)      # エッジ 1、変数 :P
EIndex(1:5, 1)     # エッジ 1 から 5 の最初の状態
EIndex(7, (:x,:y)) # エッジ 7 の状態 :x と :y
EIndex(2)          # 2 番目のエッジモデルを参照
```

`SymbolicIndexingInterface` をサポートするオブジェクトにインデックスを付けるために使用できます。例えば、[`NWState`](@ref)、[`NWParameter`](@ref) または `ODESolution`。

関連情報: [`VIndex`](@ref)、[`VPIndex`](@ref)、[`EPIndex`](@ref)

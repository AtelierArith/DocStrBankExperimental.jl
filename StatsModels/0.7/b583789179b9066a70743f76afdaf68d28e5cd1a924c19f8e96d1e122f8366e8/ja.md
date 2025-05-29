```
CategoricalTerm{C,T,N} <: AbstractTerm
```

カテゴリカル項を表し、名前と[`ContrastsMatrix`](@ref)を持ちます。

# フィールド

  * `sym::Symbol`: 変数の名前
  * `contrasts::ContrastsMatrix`: この変数が取るユニークな値と、それらが数値的予測子にどのようにマッピングされるかを捉えたコントラスト行列。

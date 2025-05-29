```
MdofMesh(Elt, constrained_dofs, free_dofs)
```

mdofメッシュを構築するためのデータを含む構造体

**コンストラクタ**

  * `model`: Mdofモデル
  * `bc`: 境界条件

      * `:CC`: クランプ - クランプ
      * `:CF`: クランプ - 自由
      * `:FF`: 自由 - 自由

**フィールド**

  * `Elt`: 要素接続行列
  * `constrained_dofs`: 制約された自由度
  * `free_dofs`: 自由な自由度

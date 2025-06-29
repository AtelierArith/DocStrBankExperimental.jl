```
Bloating{N, S<:LazySet{N}} <: LazySet{N}
```

与えられたノルムにおける集合の均一な拡張を表す型（*bloating*としても知られています）。

### フィールド

  * `X` – 集合
  * `ε` – （通常は正の）bloating因子
  * `p` – $p$-ノルム（$≥ 1$であるべき; デフォルト: $2$）

### 注意事項

`Bloating`操作は凸性を保持します：もし`X`が凸であれば、`X`の任意のbloatingも凸です。

`ε`が正であれば、`Bloating(X, ε, p)`は、`X`と半径`ε`の`p`-ノルムのボールのミンコフスキー和に相当します。原点`O`を中心とします（すなわち、`X ⊕ Ballp(p, O, ε)`）。

いくつかの操作は、`ε`が正であることを要求するか、静かに仮定します。詳細についてはドキュメントを確認してください。

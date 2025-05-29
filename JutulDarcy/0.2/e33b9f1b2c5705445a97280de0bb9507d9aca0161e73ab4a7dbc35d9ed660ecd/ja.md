```
compute_peaceman_index(g::T, K, r, pos; kwarg...) where T<:Jutul.JutulMesh
```

与えられたメッシュのためのPeacemanインデックスを計算します。

# 引数

  * `g::JutulMesh`: 貯留層メッシュ
  * `K`: 透過率テンソルまたはスカラー。
  * `r`: ウェル半径。
  * `pos`: ウェルの位置（セルのインデックスまたはIJKタプル）。
  * `kwarg...`: 関数の内部バージョンに渡される追加のキーワード引数。

# 戻り値

  * 計算されたPeacemanインデックス。

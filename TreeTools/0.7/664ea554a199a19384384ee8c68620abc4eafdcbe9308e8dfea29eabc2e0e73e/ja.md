```
SplitList{T}
```

  * `leaves::Array{T,1}`: 葉のラベル
  * `splits::Array{Split,1}`
  * `mask::Array{Bool,1}`: スプリットが適用される葉のサブセット。
  * `splitmap::Dict{T,Split}`: ノードの上のブランチに対応するスプリットを示す。内部ノードにラベルが付けられたツリーから構築された場合のみ初期化される。

# コンストラクタ

```
SplitList(leaves::Array{T,1}) where T
```

空の `SplitList`。

```
SplitList(t::Tree[, mask])
```

`t` のスプリットのリスト。`mask` はデフォルトで1の配列。

```
SplitList(r::TreeNode, leaves[, mask])
```

`r` の下にあるスプリットのリストを計算します。`r` 自体を含みます。`r` が `leaves` を持つツリーの一部であると仮定します。`mask` は `r` の子孫である葉のセットがデフォルトです。

```
remove_redundant_vertices(P::VPolygon;
                          [algorithm]::String="monotone_chain")
```

与えられたポリゴンの冗長な頂点を削除することによって得られるポリゴンを返します。

### 入力

  * `P`         – 頂点表現のポリゴン
  * `algorithm` – （オプション、デフォルト: "monotone_chain"）凸包を計算するために使用されるアルゴリズム

### 出力

与えられたポリゴンの頂点がその凸包である新しいポリゴン。

### アルゴリズム

[`remove_redundant_vertices!(::VPolygon)`](@ref)を参照してください。

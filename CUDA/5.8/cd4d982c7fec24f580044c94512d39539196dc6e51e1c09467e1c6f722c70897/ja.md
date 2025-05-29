```
CuTexture{T,N,P}(parent::P; address_mode, filter_mode, normalized_coordinates)
```

`parent`に格納されている型`T`の要素を持つ`N`次元テクスチャオブジェクトを構築します。

いくつかのキーワード引数がテクスチャオブジェクトの動作を変更します：

  * `address_mode` (wrap, *clamp*, mirror): 範囲外の値にアクセスする方法。すべての次元に対して値を指定することも、`N`エントリのタプルとして指定することもできます。
  * `interpolation` (*nearest neighbour*, linear, bilinear): 非整数インデックスが取得される方法。最近傍は単一の値を取得し、他は複数の値の間を補間します。
  * `normalized_coordinates` (true, *false*): インデックスが正規化された`[0:1)`範囲に収まることが期待されるかどうか。

!!! warning 実験的API。非推奨なしに変更される可能性があります。

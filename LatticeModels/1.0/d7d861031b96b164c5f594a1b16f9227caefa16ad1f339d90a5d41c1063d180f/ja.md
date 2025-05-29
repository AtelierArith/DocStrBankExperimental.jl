```
BravaisTranslation([site_indices, ]translate_uc)
BravaisTranslation(site_indices)
BravaisTranslation([site_indices; ]axis[, dist=1])
```

`BravaisTranslation`オブジェクトの便利なコンストラクタです。

## 引数

  * `site_indices`: 結合によって接続されるサイトのインデックスを持つ`::Int => ::Int`ペア;

省略された場合、結合は同じサブラティスインデックスを持つサイトを接続します。

  * `translate_uc`: 単位格子のオフセット。

## キーワード引数

  * `axis`: 単位格子ベクトルに関するホッピング方向軸。
  * `dist`: 単位格子ベクトルに関するホッピング距離。

`site_indices`が等しいか未定義で、`translate_uc`がゼロの場合、翻訳はすべてのサイトを自分自身に翻訳するものと見なされます。この場合、エラーが発生します。

```
braille(img; kwargs...)
braille(img, alg; kwargs...)
```

アルゴリズム `alg` を使用してバイナリダイザーを行い、ブレイルで画像を印刷します。

## キーワード引数

  * `invert`: Unicode 出力を反転させます。デフォルトは `false` です。
  * `to_string`: ターミナルに印刷する代わりに文字列を返します。デフォルトは `false` です。
  * `method`: Unicode で印刷するために使用されるメソッド。`:braille` または `:block` のいずれかです。デフォルトは `:braille` です。

バイナリダイジングメソッドのすべてのキーワード引数を使用できます。

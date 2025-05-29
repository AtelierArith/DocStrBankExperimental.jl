```
(len, point, neg) = Grisu.grisu(v::AbstractFloat, mode, requested_digits, [buffer], [bignums])
```

数値 `v` を Grisu アルゴリズムを使用して10進数に変換します。

`mode` は次のいずれかです：

  * `Grisu.SHORTEST`: `v` に「ラウンドトリップ」できる最短の10進数表現に変換します。
  * `Grisu.FIXED`: `requested_digits` 桁に丸めます。
  * `Grisu.PRECISION`: `requested_digits` 有効桁に丸めます。

文字は `buffer` にバイトとして書き込まれ、終端 NUL バイトが付加され、`bignums` は補正ステップの一部として内部で使用されます。適切なタスクローカルバッファを取得するには `Grisu.getbuf()` を呼び出すことができます。

返されるタプルには次のものが含まれます：

  * `len`: `buffer` に書き込まれた桁数（NUL を除く）
  * `point`: 配列の先頭に対する基数点の位置（例：`point == 3` の場合、基数点は3桁目と4桁目の間に挿入されるべきです）。これは非常に小さい値の場合は負になることがあり、非常に大きい値の場合は `len` より大きくなることがあります。
  * `neg`: `v` の符号ビット（[`signbit`](@ref) を参照）。

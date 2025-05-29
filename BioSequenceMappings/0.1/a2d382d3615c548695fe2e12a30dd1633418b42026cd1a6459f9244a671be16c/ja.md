```
Alignment(data::AbstractMatrix, alphabet; kwargs...)
```

`data` は整数の行列で、列にシーケンスが格納されています。`alphabet` は次のいずれかです。

  * `Alphabet`
  * `nothing`: 整数から生物学的記号への変換なし。
  * アルファベットを構築するための何か (*例*: `:aa` のようなシンボル、文字列など)。コンストラクタ `Alphabet` は次のように呼び出されます: `Alphabet(alphabet)`。

`alphabet` と `data` の型が不一致の場合、`data` は変換されます。

`data` は次の形状を持つこともできます。

  * 整数ベクトルのベクトル、*例*: [[1,2], [3,4]]: 各要素はシーケンスと見なされます
  * 整数のベクトル: 単一のシーケンスアライメント

```

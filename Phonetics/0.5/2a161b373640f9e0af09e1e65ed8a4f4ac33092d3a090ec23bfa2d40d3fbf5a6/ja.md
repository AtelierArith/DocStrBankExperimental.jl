```
area(v::VowelSpace; unstandardize=true)
```

渡された `VowelSpace` の面積 `v` を返します。

# 引数

  * `v` 面積を計算するための `VowelSpace`
  * `unstandardize` (キーワード) `v` の半正規化された F1 と F2 を Hz（または `v` が作成されたときに渡された単位）に変換するフラグ。この新しい空間で母音空間の面積を決定するために凸包が再計算されます。

# 戻り値

母音空間を囲む凸包の面積。F1 と F2 が Hz に非標準化されたときの面積の単位は Hz² です。

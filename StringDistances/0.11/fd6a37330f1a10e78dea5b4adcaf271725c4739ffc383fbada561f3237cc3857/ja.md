```
QGramDict(s, q::Integer = 2)
```

事前に計算された qgram の辞書を持つイテレータです。これにより、QGram 距離の計算が高速化されます。

qgram の長さは、距離で使用される q の長さに対応している必要があります。

## 例

```julia
str1, str2 = "my string", "another string"
qd1 = QGramDict(str1, 2)
qd2 = QGramDict(str2, 2)
evaluate(Overlap(2), qd1, qd2)
```

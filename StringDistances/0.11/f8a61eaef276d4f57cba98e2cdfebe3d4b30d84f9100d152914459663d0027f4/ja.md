```
QGramSortedVector(s, q::Integer = 2)
```

事前に計算されたソートされたベクトルを持つイテレータです。これにより、QGram距離の計算がより迅速になります。

qgramが辞書順にソートされているため、QGram距離はQGramDictを使用する場合よりもさらに迅速に計算できます。ただし、ソートされているため、作成後のカウントの更新は効率が低下します。しかし、ほとんどの使用ケースではQGramSortedVectorがQGramDictよりも好まれます。

qgramの長さは、距離で使用されるqの長さと一致する必要があります。

## 例

```julia
str1, str2 = "my string", "another string"
qs1 = QGramSortedVector(str1, 2)
qs2 = QGramSortedVector(str2, 2)
evaluate(Jaccard(2), qs1, qs2)
```

```
groupslices(V::AbstractVector)
```

`V`と同じ長さの整数ベクトルを返します。各エントリ`x`の代わりに、`x`に等しい`V`の最初のエントリのインデックスがあります。これは次のように成り立ちます：

```
all(x == V[i] for (x,i) in zip(V, groupslices(V)))
```

```
TestIterator{T,IS<:Base.IteratorSize,IE<:Base.IteratorEltype}
```

テスト目的のための構成可能なイテレータ。

```
TestIterator(data, itersize, itereltype)
TestIterator(data)
```

イテレータは、配列などの別のイテレータ `data` をラップします。これは、テストイテレータと同じだけの機能が実装されている必要があり、`FiniteDifferences.to_vec` のオーバーロードを持っている必要があります。デフォルトでは、イテレータは `data` と同じ機能を持っています。

オプションのメソッド `eltype`、`length`、および `size` は、自動的に定義され、型引数がそれらを定義する必要があることを示す場合、`data` に転送されます。

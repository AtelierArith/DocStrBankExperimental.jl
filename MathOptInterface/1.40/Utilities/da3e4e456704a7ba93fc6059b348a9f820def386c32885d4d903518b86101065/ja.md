```
Base.convert(
    ::Type{SparseMatrixCSC{Tv,Ti}},
    A::MutableSparseMatrixCSC{Tv,Ti,I},
) where {Tv,Ti,I}
```

`A`を`SparseMatrixCSC`に変換します。フィールド`A.nzval`は**コピーされない**ため、この関数の呼び出し後に`A`が変更されると、返される値に影響を与える可能性があります。さらに、`I`が`OneBasedIndexing`の場合、`colptr`と`rowval`もコピーされないため、変換はアロケーションフリーです。

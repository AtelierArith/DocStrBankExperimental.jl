```
permutedims(var::OutputVar, perm)
```

`var`の次元を`perm`に従って置換します。`perm`は置換を指定する次元名のイテラブルです。

`perm`の次元名は`var`の次元と同じである必要はありません。たとえば、`lon`と`long`という名前の次元は、経度次元として識別されます。

```
read_only_array(array::AbstractArray):AbstractArray
```

`array`の不変ビューを返します。これは`SparseArrays.ReadOnly`を使用し、`NamedArray`を適切に処理します。配列がすでに不変である場合は、そのまま返されます。

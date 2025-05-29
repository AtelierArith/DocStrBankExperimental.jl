```
abstract_nestedarray_type(T_inner::Type, ::Val{ndims_tuple})
```

ネストされた `AbstractArray` の型を返します。`T_inner` は最も内側の配列の要素型を指定し、`ndims_tuple` は各ネスト層の次元数を指定します（外側の配列が最初）。

`ndims_tuple` が空の場合、返されるのは（通常はスカラーの）型 `T_inner` 自体です。

```
ndims_extra(::Type{<:PencilArray})
ndims_extra(x::PencilArray)
ndims_extra(x::PencilArrayCollection)
```

`PencilArray`に関連する「追加」の次元の数。

これらは、ドメインの幾何学に関連付けられていない次元です。たとえば、ベクトルやテンソルの成分に対応する場合があります。

これらの次元は、配列の最右のインデックスに対応します。

`PencilArray`の次元の総数は次のように与えられます：

```
ndims(x) == ndims_space(x) + ndims_extra(x)
```

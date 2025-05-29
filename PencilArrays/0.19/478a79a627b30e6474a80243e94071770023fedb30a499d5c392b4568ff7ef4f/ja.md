```
ndims_space(x::PencilArray)
ndims_space(x::PencilArrayCollection)
```

ドメインジオメトリに関連付けられた次元の数。

これらの次元は、配列の最も左側のインデックスに対応します。

`PencilArray` の総次元数は次のように与えられます：

```
ndims(x) == ndims_space(x) + ndims_extra(x)
```

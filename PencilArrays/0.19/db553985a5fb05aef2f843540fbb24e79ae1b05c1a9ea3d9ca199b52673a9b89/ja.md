```
size_global(x::PencilArray, [order = LogicalOrder()])
size_global(x::PencilArrayCollection, [order = LogicalOrder()])
```

与えられた配列に関連付けられたグローバル次元。

デフォルトでは、データセットの論理次元が返されます。

`order = LogicalOrder()`の場合、これは`size(x)`と同じです。

関連情報として[`size_global(::Pencil)`](@ref)を参照してください。

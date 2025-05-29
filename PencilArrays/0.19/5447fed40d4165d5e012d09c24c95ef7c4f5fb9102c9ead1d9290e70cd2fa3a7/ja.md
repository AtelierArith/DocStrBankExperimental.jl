```
range_remote(x::PencilArray, coords, [order = LogicalOrder()])
range_remote(x::PencilArrayCollection, coords, [order = LogicalOrder()])
```

指定されたMPIプロセスが保持する`PencilArray`のデータ範囲を取得します。

トポロジーにおけるMPIプロセスの位置は、`coords`引数によって決定され、線形または直交インデックスとして指定できます。

詳細については、[`range_remote(::Pencil, ...)`](@ref range_remote(::Pencil, ::Integer, ::LogicalOrder))のバリアントを参照してください。

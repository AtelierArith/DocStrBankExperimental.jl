```
AcbRefMatrix <: DenseMatrix{AcbRef}
```

[`AcbMatrix`](@ref)と似ていますが、要素をインデックス指定すると、要素の`Acb`コピーの代わりに対応する要素を参照する`AcbRef`が返されます。コンストラクタは`AcbMatrix`と同じです。

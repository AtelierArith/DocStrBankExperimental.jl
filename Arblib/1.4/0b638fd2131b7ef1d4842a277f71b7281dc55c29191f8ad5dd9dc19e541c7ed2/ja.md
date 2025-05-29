```
ArbRefMatrix <: DenseMatrix{ArbRef}
```

[`ArbMatrix`](@ref)と似ていますが、要素をインデックス指定すると、要素の`Arb`のコピーではなく、対応する要素を参照する`ArbRef`が返されます。コンストラクタは`ArbMatrix`と同じです。

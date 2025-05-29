```
AcbRefVector <: DenseMatrix{AcbRef}
```

[`AcbVector`](@ref)と似ていますが、要素をインデックス指定すると、要素の`Acb`のコピーではなく、対応する要素を参照する`AcbRef`が返されます。コンストラクタは`AcbVector`と同じです。

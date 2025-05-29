```
streamfunctionfrompv!(ψh, qh, params, grid)
```

PVを反転させて、`qh`から各層の流れ関数`ψh`のフーリエ変換を取得します。`ψh = params.S⁻¹ qh`を使用します。

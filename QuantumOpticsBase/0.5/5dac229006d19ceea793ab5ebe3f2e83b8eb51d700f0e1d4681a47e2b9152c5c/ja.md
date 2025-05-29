```
displace_analytical(alpha::Number, n::Integer, m::Integer)
```

Fock基における（解析的な）変位演算子の特定の行列要素を取得します: `Dmn = ⟨n|D̂(α)|m⟩`。計算に使用される精度は`alpha`の型に基づいています。`alpha`がFloat64、ComplexF64、またはIntの場合、計算は倍精度で行われます。

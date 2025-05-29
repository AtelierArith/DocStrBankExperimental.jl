```
inverse_retract(M::ProductManifold, p, q, m::InverseProductRetraction)
```

`M`上の[`ProductManifold`](@ref)に対して、`q`に関する`p`からの逆再tractionを[`InverseProductRetraction`](@ref)を使用して計算します。デフォルトでは、これは積の各多様体に対する逆再tractionをカプセル化します。このメソッドは要素ごとに実行されるため、カプセル化された逆再tractionメソッドは各因子ごとに利用可能でなければなりません。

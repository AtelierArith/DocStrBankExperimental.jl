```
BasisFunction{B <: AbstractBSplineBasis, T}
```

単一の基底関数を説明します。

基底関数は[`BSplineBasis`](@ref)に属する場合があり（この場合、実質的にはBスプラインです）、またはBスプライン基底から派生した基底に属する場合があります（例えば、`RecombinedBSplineBasis`など）。

---

```
BasisFunction(basis::AbstractBSplineBasis, i::Int, [T = Float64])
```

指定された基底のi番目の基底関数を構築します。

構築された関数は`b(x)`として評価でき、型`T`の値を返します。

---

```
(b::BasisFunction)(x, [op::AbstractDifferentialOp])
```

座標`x`で基底関数を評価します。

導関数を評価するには、`op`引数として`Derivative(n)`を渡します。ここで、`n`は導関数の次数です。

複数の導関数を評価するには、導関数の範囲`Derivative(m:n)`を渡します。特に、`Derivative(m:n)`は基底関数自体とその最初の`n`個の導関数を評価します。

`Derivative(n) + λ Derivative(m)`のようなより一般的な微分演算子もサポートされています。

```
conjugates_arb_real(x::AbsSimpleNumFieldElem, abs_tol::Int) -> Vector{ArbFieldElem}
```

$$
x
$$

の実共役を`ArbFieldElem`型の要素として計算します。

返される配列の各エントリ$y$は`radius(y) < 2^{-abs\_tol}`を満たします。

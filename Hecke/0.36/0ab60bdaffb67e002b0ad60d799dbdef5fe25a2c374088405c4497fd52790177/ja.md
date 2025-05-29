```
conjugates_arb_log(x::AbsSimpleNumFieldElem, abs_tol::Int) -> Vector{ArbFieldElem}
```

要素 $(\log(\lvert \sigma_1(x) \rvert),\dotsc,\log(\lvert\sigma_r(x) \rvert), \dotsc,2\log(\lvert \sigma_{r+1}(x) \rvert),\dotsc, 2\log(\lvert \sigma_{r+s}(x)\rvert))$ を、半径が `2^-abs_tol` より小さい `ArbFieldElem` 型の要素として返します。

```
conjugates_arb_log(x::NumFieldOrderElem, abs_tol::Int) -> Vector{ArbFieldElem}
```

要素 $(\log(\lvert \sigma_1(x) \rvert),\dotsc,\log(\lvert\sigma_r(x) \rvert), \dotsc,2\log(\lvert \sigma_{r+1}(x) \rvert),\dotsc, 2\log(\lvert \sigma_{r+s}(x)\rvert))$ を型 `ArbFieldElem` の要素として返します。半径は `2^-abs_tol` より小さいです。

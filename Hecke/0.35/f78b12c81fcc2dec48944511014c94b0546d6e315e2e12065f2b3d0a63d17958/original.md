```
conjugates_arb_log(x::NumFieldOrderElem, abs_tol::Int) -> Vector{ArbFieldElem}
```

Returns the elements $(\log(\lvert \sigma_1(x) \rvert),\dotsc,\log(\lvert\sigma_r(x) \rvert), \dotsc,2\log(\lvert \sigma_{r+1}(x) \rvert),\dotsc, 2\log(\lvert \sigma_{r+s}(x)\rvert))$ as elements of type `ArbFieldElem` radius less then `2^-abs_tol`.

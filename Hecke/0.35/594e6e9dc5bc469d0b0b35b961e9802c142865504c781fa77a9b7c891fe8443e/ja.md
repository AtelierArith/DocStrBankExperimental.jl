```
pmaximal_overorder(O::AlgAssRelOrd, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> AlgAssRelOrd
```

順序 $O'$ を返します。これは $O$ を含み、任意の最大順序 $O''$ が $O$ を含むとき、指数 $(O'':O')$ が $p$ で割り切れないことを保証します。ここで $p$ は $O$ の基底環の素イデアルです。

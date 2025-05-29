```
  (O::NumFieldOrder)(a::NumFieldOrderElem, check::Bool = true) -> NumFieldOrderElem
```

ある順序の要素 $a$ が環 $\mathcal O$ の周囲の数体にある場合、この関数はその要素を $\mathcal O$ に強制的に変換します。`check` が `true` の場合に限り、$a$ が $\mathcal O$ に含まれていることが確認されます。

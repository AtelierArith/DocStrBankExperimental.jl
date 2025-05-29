```
  (O::NumFieldOrder)(a::NumFieldElem, check::Bool = true) -> NumFieldOrderElem
```

与えられた要素 $a$ は環 $\mathcal O$ の周囲の数体の要素です。この関数は要素を $\mathcal O$ に強制的に変換します。`check` が `true` の場合に限り、$a$ が $\mathcal O$ に含まれていることが確認されます。

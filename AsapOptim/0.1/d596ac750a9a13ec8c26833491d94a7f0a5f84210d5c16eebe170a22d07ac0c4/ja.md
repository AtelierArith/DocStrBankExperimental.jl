```
CoupledVariable(element::Asap.AbstractElement, ref::AreaVariable, factor::Float64 = 1.0)
```

`element` に対して `factor * ref.value` に結合された `AreaVariable` を作成します。

`factor` は 0 より大きくなければなりません。

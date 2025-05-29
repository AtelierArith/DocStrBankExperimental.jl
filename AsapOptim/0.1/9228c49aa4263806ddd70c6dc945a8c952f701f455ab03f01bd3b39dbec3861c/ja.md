```
CoupledVariable(element::Asap.FDMelement, ref::QVariable, factor::Float64 = 1.0)
```

`element`に対して、`factor * ref.value`に結合された`Qvariable`を作成します。

`factor`は0より大きくなければなりません。

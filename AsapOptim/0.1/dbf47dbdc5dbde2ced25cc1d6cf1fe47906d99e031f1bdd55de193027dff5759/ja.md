```
CoupledVariable(element::Asap.Element, ref::T, factor::Float64 = 1.0) where {T<:SectionVariable}

`element`に対して、`factor * ref.value`に結合された`SectionVariable`を作成します。

`factor`は0より大きくなければなりません。
```

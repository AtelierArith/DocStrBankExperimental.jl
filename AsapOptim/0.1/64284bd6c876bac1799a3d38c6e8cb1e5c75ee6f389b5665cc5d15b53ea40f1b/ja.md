```
SectionVariable <: IndependentVariable
```

要素の幾何学的セクション特性に関連付けられた変数です。

```
SectionVariable(elementindex::Int64, value::Float64, lowerbound::Float64, upperbound::Float64, property::Symbol = :A)
SectionVariable(element::Element, value::Float64, lowerbound::Float64, upperbound::Float64, property::Symbol = :A)
SectionVariable(element::Element, lowerbound::Float64, upperbound::Float64, property::Symbol = :A)
```

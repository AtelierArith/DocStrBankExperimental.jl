```
AreaVariable <: IndependentVariable
```

要素の面積に関連付けられた変数

```julia
AreaVariable(elementindex::Int64, value::Float64, lowerbound::Float64, upperbound::Float64)
AreaVariable(element::Asap.AbstractElement, value::Float64, lowerbound::Float64, upperbound::Float64)
AreaVariable(element::Asap.AbstractElement, lowerbound::Float64, upperbound::Float64)
```

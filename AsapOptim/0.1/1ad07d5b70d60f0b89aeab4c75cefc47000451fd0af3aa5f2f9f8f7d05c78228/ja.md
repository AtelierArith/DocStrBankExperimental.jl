```
Qvariable <: IndependentVariable
```

FDM要素の力密度に関連付けられた変数

```julia
QVariable(elementindex::Int64, value::Float64, lowerbound::Float64, upperbound::Float64)
QVariable(element::Asap.AbstractElement, value::Float64, lowerbound::Float64, upperbound::Float64)
QVariable(element::Asap.AbstractElement, lowerbound::Float64, upperbound::Float64)
```

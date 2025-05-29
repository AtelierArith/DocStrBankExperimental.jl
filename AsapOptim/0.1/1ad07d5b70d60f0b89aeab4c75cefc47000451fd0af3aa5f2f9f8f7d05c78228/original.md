```
Qvariable <: IndependentVariable
```

A variable tied to the force density of an FDM element

```julia
QVariable(elementindex::Int64, value::Float64, lowerbound::Float64, upperbound::Float64)
QVariable(element::Asap.AbstractElement, value::Float64, lowerbound::Float64, upperbound::Float64)
QVariable(element::Asap.AbstractElement, lowerbound::Float64, upperbound::Float64)
```

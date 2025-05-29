```
SectionVariable <: IndependentVariable
```

A variable tied to a geometric section property of an element. 

```
SectionVariable(elementindex::Int64, value::Float64, lowerbound::Float64, upperbound::Float64, property::Symbol = :A)
SectionVariable(element::Element, value::Float64, lowerbound::Float64, upperbound::Float64, property::Symbol = :A)
SectionVariable(element::Element, lowerbound::Float64, upperbound::Float64, property::Symbol = :A)
```

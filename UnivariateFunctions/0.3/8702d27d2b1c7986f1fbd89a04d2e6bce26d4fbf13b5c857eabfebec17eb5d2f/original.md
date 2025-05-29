```
Piecewise_Function <: UnivariateFunction
```

This function contants a vector of locations in the x space and a vector of UnivariateFunctions. When evaludated it uses these vectors as a lookup. It chooses the correct UnivariateFunction and evaluates it.

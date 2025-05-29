```
IndicatorMax(equations::AbstractEquations, basis; variable)
IndicatorMax(semi::AbstractSemidiscretization; variable)
```

A simple indicator returning the maximum of `variable` in an element. When constructed to be used for AMR, pass the `semi`. Pass the `equations`, and `basis` if this indicator should be used for shock capturing.

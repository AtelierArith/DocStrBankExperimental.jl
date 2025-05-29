```
presmoothing(F::NEAT, LogLinearFormula(df::Int64), LogLinearFormula(df::Int64))
```

Returns presmoothed frequency table as `SmoothedNEATFreqTab` and `glm` fitted object,  but `interval` and `marginal` elements, which are returned, are not based on smoothed score.

Preserving first C moments of original frequency data, passed `LogLinearFormula(C)` to `fml`. C is a degree of freedom

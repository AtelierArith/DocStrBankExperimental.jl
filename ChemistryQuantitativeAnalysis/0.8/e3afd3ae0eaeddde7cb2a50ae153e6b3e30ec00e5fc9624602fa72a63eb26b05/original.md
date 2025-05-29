```
weight_repr(cal::MultipleCalibration)
weight_repr(weight::Number)
```

Return string representation of `cal.weight` or `weight`. 

"none" for 0, "1/√x" for -0.5, "1/x" for -1, "1/x²" for -2,  "x^`$weight`" for other positive `weight`, and "1/x^`$(abs(weight))`" for other negative `weight`

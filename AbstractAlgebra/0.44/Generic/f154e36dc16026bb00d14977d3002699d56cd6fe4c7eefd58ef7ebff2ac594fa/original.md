```
truncate(a::AbstractAlgebra.AbsMSeries, prec::Int)
```

Return $a$ truncated to precision `prec`. This either truncates by weight in the weighted cases or truncates each variable to precision `prec` in the unweighted case.

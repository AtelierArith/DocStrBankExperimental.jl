```
SimpleKRatioOptimizer(overvoltage, favor::Vector{CharXRay} = CharXRay[], minOvervoltage=1.2)
```

Implements a simple optimizer based on shell first, overvoltage next and brightness last.  Once it picks an optimum set of lines for an element, it will not change.  You can force the selection of specific lines by including the brightest in a family in `favor`.  Lines with overvoltages less than `minOvervoltage` are not considered as available.

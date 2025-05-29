```
compactify(rational_to_compactify, radius_of_indifference)    

compactify(low=one_inteval_bound, high=other_interval_bound)
```

From all of the rational values that exist within ±`radius_of_indifference` of the `rational_to_compactify`, the interval that obtains is uniquely determines that rational for which (a) the denominator is that of least magnitude and (b) the numerator is either uniquely given or, of those available, of least magnitude.    

The first form suffers from inaccuracies due to rounding errors.    

We are indifferent to the two rational values, source and result, as magnitudes. We prefer to use the compactified value in calculations, as with it, overflow is less likely, probably, with the next arithmetic operation.

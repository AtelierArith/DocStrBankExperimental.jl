```
cross(C::InterpolationRecombinator, a, b)
```

Linear Interpolation crossover between parents `a` and `b`. The resulting individual is the addition of a scaled version of each of the parents, using `C.λ` as a control parameter.

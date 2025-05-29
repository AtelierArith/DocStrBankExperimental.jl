```
KValueWrapper(K; dependence::Symbol = :pT)
```

Create a wrapper for a K-value interpolator to be used with K-value flash.

The main purpose of this wrapper is to transform the general flash cond NamedTuple into the right arguments for multi-linear interpolation.

```
ConstantMean(field, mean_value = 1)
```

Source term for a scalar quantity $q$ with a source strength that is constant in space but dynamically adjusted in time to maintain a constant mean value $Q$ for $q$.

# Arguments

  * `field::Symbol`: The name of the quantity $q$.
  * `mean_value::Real`: The mean value $Q$ that is maintained.

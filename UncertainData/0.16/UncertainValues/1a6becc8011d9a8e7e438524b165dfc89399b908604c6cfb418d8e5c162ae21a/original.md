```
struct ConstrainedUncertainScalarValueOneParameter{S, T1 <: Number}
    distribution::Distribution{Univariate, S}
    a::T1
end
```

A constrained uncertain value represented by a one-parameter distribution, where the original distribution has been truncated.

## Fields:

  * **`distribution`**: The truncated version of the original distribution.
  * **`a`**: The original value of the parameter of the original distribution.

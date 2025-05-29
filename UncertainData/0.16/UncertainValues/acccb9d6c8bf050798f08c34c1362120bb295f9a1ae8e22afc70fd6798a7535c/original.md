```
struct ConstrainedUncertainScalarValueTwoParameter{S, T1 <: Number, T2 <: Number}
    distribution::Distribution{Univariate, S}
    a::T1
    b::T2
end
```

A constrained uncertain value represented by a two-parameter distribution, where the original distribution has been truncated.

## Fields:

  * **`distribution`**: The truncated version of the original distribution.
  * **`a`**: The original value of the first parameter of the original distribution.
  * **`b`**: The original value of the second parameter of the original distribution.

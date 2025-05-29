```
struct ConstrainedUncertainScalarValueThreeParameter{S, T1 <: Number, T2 <: Number, T3 <: Number}
    distribution::Distribution{Univariate, S}
    a::T1
    b::T2
    c::T3
end
```

A constrained uncertain value represented by a two-parameter distribution, where the original distribution has been truncated.

## Fields:

  * **`distribution`**: The truncated version of the original distribution.
  * **`a`**: The original value of the first parameter of the original distribution.
  * **`b`**: The original value of the second parameter of the original distribution.
  * **`c`**: The original value of the third parameter of the original distribution.

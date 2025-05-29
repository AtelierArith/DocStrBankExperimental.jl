```
struct OpString{T <: Number}
    coeff::T
    ops::Vector{Pair{String, Int}}
end
```

Holds operator strings (operator names with corresponding positions) along with the coefficient.

  * `coeff::T`: Coeffcient of the operator string.
  * `ops::Vector{Pair{String, Int}}`: String of operator names along with the positions.

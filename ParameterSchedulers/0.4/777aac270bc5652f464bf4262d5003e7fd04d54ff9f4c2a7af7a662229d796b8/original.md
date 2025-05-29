```
Poly{T, S<:Integer}(start, degree, max_iter)
Poly(; start, degree, max_iter)
```

A polynomial schedule decays with degree `degree`. The output conforms to

```text
start / (1 - (t - 1) / max_iter)^degree
```

# Arguments

  * `start`: the base value
  * `degree::Integer`: the degree of the polynomial
  * `max_iter::Integer`: the total number of iterations

```
expmv(t, A, b; <keyword arguments>)
```

Returns the matrix-vector product $exp(t A) b$ where `A` is a $n × n$ sparse real or complex matrix, `b` is a vector of $n$ real or complex elements and `t` is a parameter (or a `StepRangeLen` object representing a range of values).

# Arguments

  * `t`: `Number` or `StepRangeLen` object
  * `A`: a `n × n` real or complex sparse matrix
  * `b`: an `n`-vector
  * `M = []`: manually set the degree of the Taylor expansion
  * `precision = "double"`: can be `"double"`, `"single"` or `"half"`.
  * `shift = false`: set to `true` to apply a shift in order to reduce the norm of A       (see Sec. 3.1 of the paper)
  * `full_term = false`: set to `true` to evaluate the full Taylor expansion instead       of truncating when reaching the required precision

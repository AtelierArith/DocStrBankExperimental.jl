```
rec2coeff(deg::Int,a::Vector{<:Real},b::Vector{<:Real})
rec2coeff(a,b) = rec2coeff(length(a),a,b)
```

Get the coefficients of the orthogonal polynomial of degree up to `deg` specified by its recurrence coefficients `(a,b)`. The function returns the values $c_i^{(k)}$ from

$$
p_k (t) = t^d + \sum_{i=0}^{k-1} c_i t^i,
$$

where $k$ runs from `1` to `deg`.

The call `rec2coeff(a,b)` outputs all possible recurrence coefficients given `(a,b)`.

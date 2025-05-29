```
leading_exponent_vector(p::MPolyRingElem)
```

Return the exponent vector of the leading term of $p$. The return is a Julia 1-dimensional array giving the exponent for each variable of the leading term. This function throws an `ArgumentError` if $p$ is zero.

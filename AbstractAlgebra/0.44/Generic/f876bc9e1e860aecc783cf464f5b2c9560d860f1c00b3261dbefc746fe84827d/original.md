```
combine_like_terms!(a::MPoly{T}) where T <: RingElement
```

Remove zero terms and combine adjacent terms if they have the same exponent vector. The modified polynomial is returned.

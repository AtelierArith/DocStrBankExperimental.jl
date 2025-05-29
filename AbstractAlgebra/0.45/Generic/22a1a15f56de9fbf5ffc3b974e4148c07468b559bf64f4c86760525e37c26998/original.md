```
sort_terms!(a::MPoly{T}) where {T <: RingElement}
```

Sort the terms of the given polynomial according to the polynomial ring ordering. Zero terms and duplicate exponents are ignored. To deal with those call `combine_like_terms`. The sorted polynomial is returned.

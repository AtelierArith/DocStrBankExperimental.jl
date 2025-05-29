```
Spectrum!(spec::AbstractVector{Tv}, vec::AbstractVector{Tv}, size::Ti) where {Tv<:Complex, Ti<:Integer}
```

Set the spectrum from user provided vector. In fact, this function only check if the size of given spectrum vector is large enough. And they copy the first `size` elements of `vec` into `spec`.

```
χ²(s1::Spectrum{T}, s2::Spectrum{U}, chs)::T where {T<:Real, U <: Real}
χ²(specs::AbstractArray{Spectrum{T}}, chs)::Matrix{T}
```

Computes the dose corrected reduced χ² metric between `s1` and `s2` over the channels in `chs`.

The second form computes a matrix of χ² comparing each spectrum in the array to the others.

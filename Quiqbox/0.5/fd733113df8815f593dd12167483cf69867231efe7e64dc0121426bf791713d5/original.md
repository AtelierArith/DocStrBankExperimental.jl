```
GaussFunc{T, F1, F2} <: AbstractGaussFunc{T}
```

A contracted primitive Gaussian-type function.

≡≡≡ Field(s) ≡≡≡

`xpn::ParamBox{T, :α, F1}`：The exponent coefficient.

`con::ParamBox{T, :d, F2}`: The contraction coefficient.

`param::Tuple{ParamBox{T, α}, ParamBox{T, d}}`: The parameter containers  inside a `GaussFunc`.

≡≡≡ Initialization Method(s) ≡≡≡

```
GaussFunc(e::Union{T, Array{T, 0}, ParamBox{T}}, d::Union{T, ParamBox{T}}) where 
         {T<:AbstractFloat} -> 
GaussFunc{T}
```

```
struct NonnegPolyInnerCone{MCT <: MOI.AbstractVectorSet}
end
```

Inner approximation of the cone of nonnegative polynomials defined by the set of polynomials of the form

```julia
X^\top Q X
```

where `X` is a vector of monomials and `Q` is a symmetric matrix that belongs to the cone `psd_inner`.

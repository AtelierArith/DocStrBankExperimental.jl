```
norm(a::AbstractSequence, p::Real=Inf)
```

Compute the `p`-norm of `a`. Only `p` equal to `1`, `2` or `Inf` is supported.

This is equivalent to:

  * `norm(a, Ell1(IdentityWeight()))` if `p == 1`
  * `norm(a, Ell2(IdentityWeight()))` if `p == 2`
  * `norm(a, EllInf(IdentityWeight()))` if `p == Inf`

See also: [`norm(::Sequence, ::BanachSpace)`](@ref).

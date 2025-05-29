```julia
has_expmv!(L)

```

Check if `expmv!(w, L, v, t)`, equivalent to `mul!(w, exp(t * A), v)`, is defined for `Number` `t`, and `AbstractArray`s `w, v` of appropriate sizes.

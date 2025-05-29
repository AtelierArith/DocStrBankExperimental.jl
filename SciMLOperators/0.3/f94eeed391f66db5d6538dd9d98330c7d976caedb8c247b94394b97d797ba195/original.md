```julia
has_expmv!(L)

```

Check if `expmv!(v, L, u, t)`, equivalent to `mul!(v, exp(t * A), u)`, is defined for `Number` `t`, and `AbstractArray`s `u, v` of appropriate sizes.

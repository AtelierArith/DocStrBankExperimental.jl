```julia
has_expmv(L)

```

Check if `expmv(L, u, t)`, equivalent to `exp(t * A) * u`, is defined for `Number` `t`, and `AbstractArray` `u` of appropriate size.

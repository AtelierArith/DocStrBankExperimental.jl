```
r⁻¹(r, pnsystem)
separation_inverse(r, pnsystem)
```

Return `v` such that `r = r(v)` when `pnsystem` is evaluated at `v`.

Note that the value of `v` in the input `pnsystem` is ignored; you may use any value.  It may also be convenient to know that you can set the value of `v` in `pnsystem` to the returned value using `PostNewtonian.vindex` as in

```julia
pnsystem.state[PostNewtonian.vindex] = r⁻¹(r, pnsystem)
```

See also [`γₚₙ⁻¹`](@ref).

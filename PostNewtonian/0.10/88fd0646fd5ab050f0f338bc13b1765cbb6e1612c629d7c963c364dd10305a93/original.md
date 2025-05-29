```
γₚₙ⁻¹(γ, pnsystem)
inverse_separation_inverse(γ, pnsystem)
```

Return `v` such that `γₚₙ(pnsystem) = γ` when `pnsystem` is evaluated at `v`.

Note that the value of `v` in the input `pnsystem` is ignored; you may use any value.  It may also be convenient to know that you can set the value of `v` in `pnsystem` to the returned value using `PostNewtonian.vindex` as in

```julia
pnsystem.state[PostNewtonian.vindex] = γₚₙ⁻¹(γ, pnsystem)
```

See also [`r⁻¹`](@ref).

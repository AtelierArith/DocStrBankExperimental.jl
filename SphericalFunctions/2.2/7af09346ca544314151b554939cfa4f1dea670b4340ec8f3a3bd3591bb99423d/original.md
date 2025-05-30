```
map2salm(map, spin, ℓmax)
map2salm(map, plan)
```

Transform `map` values sampled on the sphere to ${}_sa_{\ell, m}$ modes.

The `map` array should have size Nφ along its first dimension and Nϑ along its second; any number of dimensions may follow.  The `spin` must be entered explicitly, and `ℓmax` is the highest ℓ value you want in the output.

For repeated applications of this function with different values of `map`, it is more efficient to pre-compute `plan` using [`plan_map2salm`](@ref).  These functions will create a new `salm` array on each call.  To operate in place on a pre-allocated `salm` array, use [`map2salm!`](@ref).

The core of this function follows the method described by [Reinecke and Seljebotn](@cite Reinecke_2013).

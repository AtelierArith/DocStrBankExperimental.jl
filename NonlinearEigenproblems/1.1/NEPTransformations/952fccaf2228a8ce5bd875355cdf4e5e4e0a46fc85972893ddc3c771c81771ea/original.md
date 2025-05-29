```
shift_and_scale(orgnep::NEP;shift=0,scale=1)
```

Transforms the orgnep by defining a new NEP from the relation T(λ)=M(scale * λ+shift) where M is the orgnep. This function tries  to preserve the NEP type, e.g., a shift*and*scale operation on an SPMF-object, return an SPMF object. If it cannot preserve the type, it will return a nep of the struct `ShiftScaledNEP`.

# Example

```julia-repl
julia> nep0=nep_gallery("pep0")
julia> σ=3; α=10;
julia> nep1=shift_and_scale(nep0,shift=σ,scale=α)
julia> opnorm(compute_Mder(nep0,α*(4+4im)+σ)-compute_Mder(nep1,4+4im))
8.875435870738592e-12
```

```
compute_Mder(nep::NEP,λ::Number [,i::Integer=0])
```

Computes the ith derivative of `nep` evaluated in `λ`.

# Example

This example shows that `compute_Mder(nep,λ,1)` gives the first derivative.

```julia-repl
julia> nep=nep_gallery("dep0");
julia> ϵ=1e-5; λ=2.25;
julia> Aminus=compute_Mder(nep,λ-ϵ);
julia> Aplus=compute_Mder(nep,λ+ϵ);
julia> opnorm((Aplus-Aminus)/(2ϵ)-compute_Mder(nep,λ,1))
1.8783432885257602e-11
```

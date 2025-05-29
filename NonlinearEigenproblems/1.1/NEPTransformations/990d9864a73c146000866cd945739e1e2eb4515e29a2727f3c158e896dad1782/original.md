```
mobius_transform(orgnep::NEP,[,a=1][,b=0][,c=0][,d=1])
```

Transforms a nep (orgnep) $M(λ)v$ to a new nep $T(λ)=M((aλ+b)/(cλ+d))$. This function tries to preserve the type such that `T` and `M` are of the same NEP-type (see `shift_and_scale()`). If it cannot be preserved it will return a `MobiusTransformedNEP`. It is in general advised to try to preserve the type, and the use of `MobiusTransformedNEP` can considerably slow down NEP-access.

# Example

```julia-repl
julia> nep0=nep_gallery("pep0")
julia> a=1; b=3; c=4; d=5;
julia> nep1=mobius_transform(nep0,a=a,b=b,c=c,d=d);
julia> s=3;
julia> opnorm(compute_Mder(nep0,(a*s+b)/(c*s+d))-compute_Mder(nep1,s))
0.0
```

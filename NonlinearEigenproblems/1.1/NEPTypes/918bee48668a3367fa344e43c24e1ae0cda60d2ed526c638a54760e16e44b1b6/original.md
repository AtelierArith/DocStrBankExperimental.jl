```
struct StandardSPMFErrmeasure <: Errmeasure
function StandardSPMFErrmeasure(nep::AbstractSPMF)
```

This `Errmeasure` provides a way to compute the backward error. The backward error estimate are only given for NEPs which are subtypes of  `AbstractSPMF`. We use the Frobenius norm as the matrix norm, since it is much cheaper to compute than the spectral norm.

# Example

```julia
julia> nep=nep_gallery("qdep0");
julia> (λ,v)=quasinewton(nep,λ=-1,v=ones(size(nep,1)),errmeasure=StandardSPMFErrmeasure(nep),tol=1e-10,logger=1);
Precomputing linsolver
iter 1 err:0.022010375110869937 λ=-1.0 + 0.0im
iter 2 err:0.002515422247048546 λ=-0.7063330111559607 + 0.0im
iter 3 err:0.000892354247568813 λ=-0.8919579082730457 + 0.0im
iter 4 err:5.445678793151584e-5 λ=-1.0097584042560848 + 0.0im
iter 5 err:6.649967517409105e-7 λ=-1.0023823873044 + 0.0im
iter 6 err:1.0557281809769784e-8 λ=-1.0024660870524031 + 0.0im
iter 7 err:6.420125566431444e-9 λ=-1.0024677891861997 + 0.0im
iter 8 err:3.181093707909799e-10 λ=-1.0024669496893164 + 0.0im
iter 9 err:2.6368050026394416e-11 λ=-1.0024669918249076 + 0.0im

```

See also: [`Errmeasure`](@ref)

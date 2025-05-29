```
struct EigvalReferenceErrmeasure{X<:Number} <: Errmeasure
function EigvalReferenceErrmeasure(nep,λref)
```

Use the difference between a precomputed λ-value (reference solution) and the eigenvalue estimate as the error measure.

# Example

```julia
julia> using LinearAlgebra
julia> nep=nep_gallery("qdep0");
julia> (λref,vref)=quasinewton(nep,λ=-1,v=ones(size(nep,1)));
julia> (λ,v)=quasinewton(nep,errmeasure=EigvalReferenceErrmeasure(nep,λref),λ=-1.0 ,logger=1,tol=5e-13,v=ones(size(nep,1)));
Precomputing linsolver
iter 1 err:0.002466988585763996 λ=-1.0 + 0.0im
iter 2 err:0.2961339774298033 λ=-0.7063330111559607 + 0.0im
iter 3 err:0.11050908031271833 λ=-0.8919579082730457 + 0.0im
iter 4 err:0.007291415670320767 λ=-1.0097584042560848 + 0.0im
iter 5 err:8.460128136400513e-5 λ=-1.0023823873044 + 0.0im
iter 6 err:9.015333608530796e-7 λ=-1.0024660870524031 + 0.0im
iter 7 err:8.006004357241636e-7 λ=-1.0024677891861997 + 0.0im
iter 8 err:3.889644761834177e-8 λ=-1.0024669496893164 + 0.0im
iter 9 err:3.2391436199930013e-9 λ=-1.0024669918249076 + 0.0im
iter 10 err:2.418474309706653e-10 λ=-1.0024669883439166 + 0.0im
iter 11 err:2.0230705999324528e-11 λ=-1.0024669886059947 + 0.0im
iter 12 err:0.0 λ=-1.002466988585764 + 0.0im
```

See also: [`Errmeasure`](@ref)

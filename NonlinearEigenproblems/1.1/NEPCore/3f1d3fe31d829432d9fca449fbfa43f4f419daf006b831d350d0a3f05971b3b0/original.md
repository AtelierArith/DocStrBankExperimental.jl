```
compute_Mlincomb(nep::NEP,λ::Number,V, a::Vector=ones(size(V,2)), startder=0)
compute_Mlincomb!(nep::NEP,λ::Number,V, a::Vector=ones(size(V,2)), startder=0)
```

Computes the linear combination of derivatives
$Σ_i a_i M^{(i)}(λ) v_i$ starting from derivative `startder`. The function `compute_Mlincomb!` does the same but may modify the `V` matrix/array.

# Example

This example shows that `compute_Mder` gives a result consistent with `compute_Mlincomb`. Note that `compute_Mlincomb` is in general faster since no matrix needs to be constructed.

```julia-repl
julia> nep=nep_gallery("dep0");
julia> v=ones(size(nep,1)); λ=-1+1im;
julia> norm(compute_Mder(nep,λ,1)*v-compute_Mlincomb(nep,λ,hcat(v,v),[0,1]))
0.0
```

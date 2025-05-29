```
FourierBasis([::Type,] num_inputs::Int, dorder::Int, iorder::Int [, full::Bool=false])
```

Creates a struct to generate fourier features up to a given order. Both coupled fourier features, e.g.,  $\cos(π(3x₁ + 2x₂))$ and uncoupled features, $[\cos(πx₁), \cos(π2x₁), …]$ can be generated with this basis function.  The dorder parameter controls order for the coupling features. The number of coupled features generated, $(\text{dorder}+1)^{\text{num\_inputs}}$,  grows exponentially with dorder, so it is not reccomended for use with high deminsional vectors. The iorder parameter controls the order of the independent features generated. The full parameter determines if both  $\sin$ and $\cos$ features are generated, if false only cos features are generated. 

See also: [`FourierBasisBuffer`](@ref)

# Examples

```jldoctest
julia> f = FourierBasis(2, 1, 2);

julia> x = [0.0, 0.5];

julia> feats = f(x)
6-element Array{Float64,1}:
  1.0
  6.123233995736766e-17
  1.0
  6.123233995736766e-17
  1.0
 -1.0

```

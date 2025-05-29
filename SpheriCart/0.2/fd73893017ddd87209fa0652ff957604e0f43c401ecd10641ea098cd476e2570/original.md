`struct SolidHarmonics` : datatype representing a solid harmonics basis. 

### Constructor to generate the basis object

```julia
basis = SolidHarmonic(L::Integer; kwargs...)
```

### Keyword arguments:

  * `normalisation = :L2` : choose the normalisation of the basis, default is to   make it orthonormal on the unit sphere.
  * `static = (L<=15)` : decide whether to use a generated code that outputs an

`SVector` but has a larger compiler and stack footprint

  * `T = Float64` : datatype in which basis parameters are stored. The output type

is inferred at runtime, but the rule of thumb is to use `T = FloatX` for  `FloatX` output.

### Usage example:

```julia
using StaticArrays, SpheriCart
basis = SolidHarmonics(4)
# evaluate basis with single input 
𝐫 = @SVector randn(3)
Z = basis(𝐫)
Z = compute(basis, 𝐫)
# evaluate basis with multiple inputs (batching)
R = [ @SVector randn(3) for _ = 1:32 ]
Z = basis(Rs)
Z = compute(basis, Rs)
# evaluate basis with gradients
Z, ∇Z = compute_with_gradients(basis, 𝐫) # or Rs

# to be implented: (simply use ForwardDiff)
# Z, ∇Z, ∇²Z = compute_with_hessian(basis, 𝐫)
```

See documentation for more details.

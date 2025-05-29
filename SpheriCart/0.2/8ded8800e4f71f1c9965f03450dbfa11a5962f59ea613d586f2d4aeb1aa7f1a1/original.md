`struct SphericalHarmonics` : datatype representing a real spherical harmonics basis. 

### Constructor to generate the basis object

```julia
basis = SphericalHarmonics(L::Integer; kwargs...)
```

### Keyword arguments:

  * `normalisation = :L2` : choose the normalisation of the basis, default is to   make it orthonoormal on the unit sphere.
  * `static = (L<=15)` : decide whether to use a generated code that outputs an

`SVector` but has a larger compiler and stack footprint

  * `T = Float64` : datatype in which basis parameters are stored. The output type

is inferred at runtime, but the rule of thumb is to use `T = FloatX` for  `FloatX` output.

### Usage example:

```julia
using StaticArrays, SpheriCart
basis = SphericalHarmonics(4)
# evaluate basis with single input 
𝐫 = @SVector randn(3)
Z = basis(𝐫)
Z = compute(basis, 𝐫)
# evaluate basis with multiple inputs (batching)
R = [ @SVector randn(3) for _ = 1:32 ]
Z = basis(Rs)
Z = compute(basis, Rs)

# to be implented: 
# Z, ∇Z = compute_and_gradients(basis, 𝐫)
# Z, ∇Z, ∇²Z = compute_and_hessian(basis, 𝐫)
```

See documentation for more details.

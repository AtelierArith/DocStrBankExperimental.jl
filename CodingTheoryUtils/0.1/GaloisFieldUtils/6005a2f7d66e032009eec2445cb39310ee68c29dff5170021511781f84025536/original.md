```
get_minimum_polynomial(β::F)::Polynomial{F} where F <: GaloisFields.AbstractExtensionField
```

Calculate the minimal polynomial of a finite field element.

# Arguments

  * `β`: A finite field element

# Returns

  * `Polynomial{F}`: The minimal polynomial of the element

# Examples

```julia
julia> F4 = @GaloisField 2^2
julia> α = primitiveroot(F4)
julia> get_minimum_polynomial(α)
Polynomial(1 + x + x^2)
```

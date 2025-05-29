```
get_roots(px::Polynomial{F})::Array{F,1} where F <: GaloisFields.AbstractExtensionField
```

Calculate the roots of a polynomial over a finite field.

# Arguments

  * `px`: A polynomial over a finite field

# Returns

  * `Array{F,1}`: An array of the polynomial's roots

# Examples

```julia
julia> F4, α = GaloisField(2, 2, :α)
julia> p = Polynomial([F4(1), F4(1), F4(1)])  # x^2 + x + 1
julia> get_roots(p)
2-element Array{GaloisField{2,2},1}:
 α
 α^2
```

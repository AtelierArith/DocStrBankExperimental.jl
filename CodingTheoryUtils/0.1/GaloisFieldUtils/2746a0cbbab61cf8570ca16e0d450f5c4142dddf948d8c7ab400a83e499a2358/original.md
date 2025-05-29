```
make_companion_matrix(a::F, α::F)::Matrix{F2} where F <: GaloisFields.AbstractGaloisField
```

Generate a companion matrix from a finite field element and its primitive root.

# Arguments

  * `a::F`: A finite field element
  * `α::F`: The primitive root of the field

# Returns

  * `Matrix{F2}`: Companion matrix

# Examples

```julia
F4, α = GaloisField(2, 2, :α)
A = make_companion_matrix(α, α)
```

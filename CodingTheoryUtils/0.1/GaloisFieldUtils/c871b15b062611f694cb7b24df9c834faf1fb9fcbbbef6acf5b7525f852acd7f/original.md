```
get_conjugates(β::F)::Array{F,1} where F <: GaloisFields.AbstractExtensionField
```

Calculate the conjugates of a finite field element.

# Arguments

  * `β`: A finite field element

# Returns

  * `Array{F,1}`: An array of the element's conjugates

# Examples

```julia
julia> F4 = @GaloisField 2^2
julia> α = primitiveroot(F4)
julia> get_conjugates(α)
2-element Array{GaloisField{2,2},1}:
 α
 α^2
```

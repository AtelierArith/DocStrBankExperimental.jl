```
gf_pretty(a::F, α::F)::String where F <: GaloisFields.AbstractGaloisField
```

Pretty print a Galois field element in the form "α^p".

# Arguments

  * `a::F`: The Galois field element to print.
  * `α::F`: The primitive element of the field used as the base.

# Returns

  * `String`: The string representation "α^p" or "0" if the element is zero.

# Examples

```julia
F4, α = GaloisField(4, :α)
gf_pretty(α, α) == "α^1"
gf_pretty(F4(1), α) == "α^0"
gf_pretty(F4(0), α) == "0"
```

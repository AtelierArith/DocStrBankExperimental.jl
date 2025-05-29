```
get_order(x::F) where F <: GaloisFields.AbstractGaloisField
```

Calculate the order of a finite field element.

# Arguments

  * `x::F`: A finite field element

# Returns

  * `Int`: The order of the element. If the element is zero, returns -1.

# Examples

```julia
F4, α = GaloisField(2, 2, :α)
get_order(α)  # 3
get_order(F4(1))  # 1
get_order(F4(0))  # -1
```

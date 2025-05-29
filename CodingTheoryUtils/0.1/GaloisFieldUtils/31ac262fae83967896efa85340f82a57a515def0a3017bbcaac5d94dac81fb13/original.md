```
get_order(genpoly::Polynomial{F}) where F <: GaloisFields.AbstractGaloisField
```

Calculate the order of a polynomial.

# Arguments

  * `genpoly::Polynomial{F}`: A polynomial over a finite field

# Returns

  * `Int`: The order of the polynomial

# Examples

```julia
F2 = @GaloisField 2
p = Polynomial([F2(1), F2(1), F2(1)])  # x^2 + x + 1
get_order(p)  # 3
```

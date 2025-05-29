```
@bra(name, basis=SpinBasis(1//2))
```

Define a symbolic bra of type `SBra`. By default, the defined basis is the spin-1/2 basis.

```jldoctest
julia> @bra b₁
⟨b₁|

julia> @bra b₂ FockBasis(2)
⟨b₂|
```

```
@ket(name, basis=SpinBasis(1//2))
```

Define a symbolic ket of type `SKet`. By default, the defined basis is the spin-1/2 basis.

```jldoctest
julia> @ket k₁
|k₁⟩

julia> @ket k₂ FockBasis(2)
|k₂⟩
```

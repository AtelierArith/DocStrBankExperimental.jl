```
@op(name, basis=SpinBasis(1//2))
```

Define a symbolic operator of type `SOperator`. By default, the defined basis is the spin-1/2 basis.

```jldoctest
julia> @op A
A

julia> @op B FockBasis(2)
B
```

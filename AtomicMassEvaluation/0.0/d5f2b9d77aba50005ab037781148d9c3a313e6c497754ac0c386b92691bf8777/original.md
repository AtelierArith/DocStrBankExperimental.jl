```
struct Isotope
    Z::Int
    N::Int
end
```

Isotope struct, constructors as follows:

```julia
Isotope(iso::Isotope)
Isotope(Z::Integer, N::Integer)
Isotope(name::AbstractString) # parse the name of the isotope, e.g. `Ne20`
```

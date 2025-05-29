```
conventionalize(flat::AbstractFourierLattice, cntr::Char) --> ::typeof(flat′)
```

Given `flat` referred to a primitive basis with centering `cntr`, compute the derived (but physically equivalent) lattice `flat′` referred to the associated conventional basis. 

See also the complementary method [`primitivize(::AbstractFourierLattice, ::Char)`](@ref) for additional details.

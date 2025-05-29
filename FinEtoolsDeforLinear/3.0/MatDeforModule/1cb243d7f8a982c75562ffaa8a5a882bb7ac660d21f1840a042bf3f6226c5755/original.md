```
tens4symmtto6x6t!(M::Matrix{T}, ST::Array{T, 4}) where {T}
```

Convert a symmetric 4th-order tensor to a 6 x 6 matrix.

!!! Note The order corresponds to the arrangement of the components of stress (or strain) tensor, symmetric, three-dimensional, into a 6-component  vector.

# Example

```
J=tens4_ijkl(eye(3),eye(3))
produces the tracor:
T=rand(3); 
sum(diag(T))*eye(3)
t= tens4_dot_2(J,T)
M= tens4_symm_to_6(ST)
```

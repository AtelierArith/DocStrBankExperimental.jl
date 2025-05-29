```
changeHbasis(twoBodyInt::AbstractArray{T, 4}, 
             C1::AbstractMatrix{T}, C2::AbstractMatrix{T}) where {T} -> 
AbstractArray{T, 4}
```

Change the basis of the input two-body integrals `twoBodyInt` based on two orbital  coefficient matrices `C1` and `C2` for different spin configurations (e.g., the  unrestricted case). The output is a 3-element `Tuple` of which the first 2 elements are the  spatial integrals of each spin configurations respectively, while the last element is the  Coulomb interactions between orbitals with different spins.

```
get_coordinates(::SymmetricPositiveDefinite, p, X, ::DefaultOrthonormalBasis)
```

Using the basis from [`get_basis`](@ref get_basis(M::SymmetricPositiveDefinite,p,B::DefaultOrthonormalBasis{<:Any,ManifoldsBase.TangentSpaceType})) the coordinates with respect to this ONB can be simplified to

$$
   c_k = \mathrm{tr}(p^{-\frac{1}{2}}\Delta_{i,j} X)
$$

where $k$ is trhe linearized index of the $i=1,\ldots,n, j=i,\ldots,n$.

```
get_vector(::SymmetricPositiveDefinite, p, c, ::DefaultOrthonormalBasis)
```

Using the basis from [`get_basis`](@ref  get_basis(M::SymmetricPositiveDefinite,p,B::DefaultOrthonormalBasis{<:Any,ManifoldsBase.TangentSpaceType})) the vector reconstruction with respect to this ONB can be simplified to

$$
   X = p^{\frac{1}{2}} \Biggl( \sum_{i=1,j=i}^n c_k \Delta_{i,j} \Biggr) p^{\frac{1}{2}}
$$

where $k$ is the linearized index of the $i=1,\ldots,n, j=i,\ldots,n$.

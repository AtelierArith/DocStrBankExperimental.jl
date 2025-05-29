```
mgs(X::𝕄{T}, numCol::Int=0) where T<:RealOrComplex
```

Modified (stabilized) [Gram-Schmidt orthogonalization](https://bit.ly/2YE6zvy)  of the columns of square or tall matrix $X$, which can be comprised of real  or complex elements.  The orthogonalized $X$ is returned by the function. $X$ is not changed.

All columns are orthogonalized by default. If instead argument `numCol` is provided,  then only the first `numCol` columns of $X$ are orthogonalized.  In this case only the firt `numCol` columns will be returned.

**Examples**

```julia
using LinearAlgebra, PosDefManifold
X=randn(10, 10);
U=mgs(X)        # result is 10⋅10
U=mgs(X, 3)     # result is 10⋅3
U'*U ≈ I ? println(" ⭐ ") : println(" ⛔ ")
# julia undertands also:
U'U ≈ I ? println(" ⭐ ") : println(" ⛔ ")
```

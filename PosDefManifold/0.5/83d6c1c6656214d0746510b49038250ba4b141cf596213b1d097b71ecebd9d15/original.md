```
gram(X::Matrix{T}) where T<:RealOrComplex
```

Given a generic data matrix $X$, comprised of real or complex elements,  return the normalized [Gram matrix](https://bit.ly/2I0FQn2), that is,  the covariance matrix of $X$  corrected by sample size, but without subtracting the mean.

The result is flagged as `Hermitian`.  See [typecasting matrices](@ref).

!!! note "Nota Bene"
    If $X$ is wide or square (r<=c) return $XX^H/c$. If $X$ is tall (r>c)            return $X^HX/r$.


**Examples**

```julia
using PosDefManifold
X=randn(5, 150);
G=gram(X) # => G=X*X'/150
X=randn(100, 2);
F=gram(X); # => G=X'*X/100
```

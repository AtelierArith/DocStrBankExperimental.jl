```
fht(A [, dims])
```

Performs a multidimensional Fast Hartley Transform (FHT) of the array `A`. The optional `dims` argument specifies an iterable subset of dimensions  (e.g. an integer, range, tuple, or array) to transform along. Most efficient if the size of `A` along the transformed dimensions is a product of small primes; see `Base.nextprod`. See also [`plan_fht()`](@ref) for even greater efficiency.

A one-dimensional FHT computes the one-dimensional discrete Hartley transform (DHT) as defined by

$$
\operatorname{DFT}(A)[k] = \sum_{n=1}^{\operatorname{length}(A)} \operatorname{cas} \left( +i\frac{2\pi(n-1)(k-1)}{\operatorname{length}(A)} \right) A[n],
$$

where $\operatorname{cas}$ is the cosine-and-sine function, or alternatively called Hartley kernel, defined by

$$
\operatorname{cas}(x) = \cos(x) + \sin(x).
$$

A multidimensional FHT simply performs this operation along each transformed dimension of `A`.

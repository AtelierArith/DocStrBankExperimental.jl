```
ntt(x::Array{T,1}, g, q) -> Array{T,1}
```

The [Number Theoretic Transform](https://en.wikipedia.org/wiki/Discrete_Fourier_transform_(general)#Number-theoretic_transform) transforms data in a similar fashion to DFT, but instead complex roots of unity it uses integer roots with all operation defined in a finite field (modulo an integer number).

`ntt` function implements Number Theoretic Transform directly from the formula, so it is flexible about choosing transformation params but lacks performance.

$\bar{x}_k = \sum_{n=1}^N{x_n g^{(n-1)(k-1)} } \mod q$

There is also a few constraints on choosing parameters and input length to ensure that inverse exists and equals to the original input:

  * $g$ must $N$-th root of one in modulo $q$ arithmetic
  * $q-1$ mod $N$ must be equal zero
  * $q$ must be grater than maximum element present in transformed array

To find parameter set you may use fint-ntt script.

The arguments of `ntt` function are

  * `x`: input data, its elements must be smaller than q
  * `g`: transform power base, must have inversion modulo q
  * `q`: defines modulo arithmetic

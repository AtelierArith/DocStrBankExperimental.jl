```
TensorSpace(a::Space,b::Space)
```

represents a tensor product of two 1D spaces `a` and `b`. The coefficients are interlaced in lexigraphical order.

For example, consider

```julia
Fourier()*Chebyshev()  # returns TensorSpace(Fourier(),Chebyshev())
```

This represents functions on `[-π,π) x [-1,1]`, using the Fourier basis for the first argument and Chebyshev basis for the second argument, that is, `φ_k(x)T_j(y)`, where

```
φ_0(x) = 1,
φ_1(x) = sin x,
φ_2(x) = cos x,
φ_3(x) = sin 2x,
φ_4(x) = cos 2x
…
```

By Choosing `(k,j)` appropriately, we obtain a single basis:

```
φ_0(x)T_0(y) (= 1),
φ_0(x)T_1(y) (= y),
φ_1(x)T_0(y) (= sin x),
φ_0(x)T_2(y), …
```

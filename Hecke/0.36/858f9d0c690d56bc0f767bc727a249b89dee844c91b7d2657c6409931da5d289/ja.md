```
bad_primes(L::HermLat; discriminant::Bool = false, dyadic::Bool = false)
                                                         -> Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}
```

与えられたエルミート格子 `L` が $E/K$ 上にある場合、`L` のスケールまたは体積を割る $\mathcal O_K$ の素イデアルを返します。

`discriminant == true` の場合、$\mathcal O_E$ の判別式を割る素イデアルが返されます。`dyadic == true` の場合、$2*\mathcal O_K$ を割る素イデアルが返されます。

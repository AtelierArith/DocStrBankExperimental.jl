```
exp(A::AbstractMatrix)
```

Calcula la exponencial de la matriz `A`, definida por

$$
e^A = \sum_{n=0}^{\infty} \frac{A^n}{n!}.
$$

Para `A` simétrica o hermítica, se utiliza una descomposición en valores propios ([`eigen`](@ref)), de lo contrario se elige el algoritmo de escalado y cuadrado (ver [^H05]).

[^H05]: Nicholas J. Higham, "The squaring and scaling method for the matrix exponential revisited", SIAM Journal on Matrix Analysis and Applications, 26(4), 2005, 1179-1193. [doi:10.1137/090768539](https://doi.org/10.1137/090768539)

# Ejemplos

```jldoctest
julia> A = Matrix(1.0I, 2, 2)
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0

julia> exp(A)
2×2 Matrix{Float64}:
 2.71828  0.0
 0.0      2.71828
```

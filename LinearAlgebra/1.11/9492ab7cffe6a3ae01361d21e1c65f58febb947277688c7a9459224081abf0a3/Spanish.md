```
eigen(A, B; sortby) -> GeneralizedEigen
```

Calcula la descomposición de valores propios generalizados de `A` y `B`, devolviendo un objeto de factorización [`GeneralizedEigen`](@ref) `F` que contiene los valores propios generalizados en `F.values` y los vectores propios generalizados en las columnas de la matriz `F.vectors`. Esto corresponde a resolver un problema de valores propios generalizados de la forma `Ax =  λBx`, donde `A, B` son matrices, `x` es un vector propio, y `λ` es un valor propio. (El `k`-ésimo vector propio generalizado se puede obtener de la porción `F.vectors[:, k]`.)

Iterar la descomposición produce los componentes `F.values` y `F.vectors`.

Por defecto, los valores propios y vectores se ordenan lexicográficamente por `(real(λ),imag(λ))`. Se puede pasar una función de comparación diferente `by(λ)` a `sortby`, o se puede pasar `sortby=nothing` para dejar los valores propios en un orden arbitrario.

# Ejemplos

```jldoctest
julia> A = [1 0; 0 -1]
2×2 Matrix{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 Matrix{Int64}:
 0  1
 1  0

julia> F = eigen(A, B);

julia> F.values
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> F.vectors
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```

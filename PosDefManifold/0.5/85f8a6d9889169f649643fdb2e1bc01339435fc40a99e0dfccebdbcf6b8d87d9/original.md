```
(1) quadraticForm(v::Vector{T}, P::ℍ{T}) where T<:Real
(2) quadraticForm(v::Vector{T}, L::𝕃{T}) where T<:Real
(3) quadraticForm(v::Vector{T}, X::𝕄{T}, forceLower::Bool=false) where T<:Real
(4) quadraticForm(v::Vector{S}, X::Union{𝕄{S}, ℍ{S}, 𝕃{S}}) where S<:Complex
```

**alias**: `qf`

(1) Given a real vector $v$ and a real `Hermitian` matrix $P$,  compute the quadratic form

$v^TPv$,

where the superscript *T* denotes transpose.  It uses only the lower triangular part of $P$.

(2) As in (1), given a real vector $v$  and a `LowerTriangular` matrix $L$.

(3) As in (1), given a real vector $v$  and a real generic `Matrix` $M$, if `forceLower=true`. If `forceLower=false`,  the product $v^TMv$ is evaluated instead using the whole matrix $M$.

(4) Quadratic form $v^HPv$, where superscript *H* denotes complex conjugate  and transpose, for a complex vector `v` and a complex `Matrix`, `LowerTrianglar`  or `Hermitian` matrix.  The whole matrix is used.

## Math

For $v$ and $X$ real and $X$ symmetric, the quadratic form is

$\sum_i(v_i^2x_{ii})+\sum_{i>j}(2v_iv_jx_{ij})$.

For $L$ lower triangular is

$\sum_i(v_i^2x_{ii})+\sum_{i>j}(v_iv_jx_{ij})$.

These formula are used in methods (1), (2) and (3).

**Examples**

```julia
using PosDefManifold
P=randP(5) # generate a random real positive definite matrix 5x5
v=randn(5)
q1=quadraticForm(v, P) # or q1=qf(v, P)
q2=v'*P*v
q1 ≈ q2 ? println(" ⭐ ") : println(" ⛔ ")
```

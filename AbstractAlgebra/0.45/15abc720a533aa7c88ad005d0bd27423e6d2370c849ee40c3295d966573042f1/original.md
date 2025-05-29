```
nullspace(M::MatElem{T}) where {T <: RingElement}
```

Return a tuple $(\nu, N)$ consisting of the nullity $\nu$ of $M$ and a basis $N$ (consisting of column vectors) for the right nullspace of $M$, i.e. such that $MN$ is the zero matrix. If $M$ is an $m\times n$ matrix $N$ will be an $n\times \nu$ matrix. Note that the nullspace is taken to be the vector space kernel over the fraction field of the base ring if the latter is not a field. In AbstractAlgebra we use the name "kernel" for a function to compute an integral kernel.

# Examples

```jldoctest
julia> R, x = polynomial_ring(ZZ, :x)
(Univariate polynomial ring in x over integers, x)

julia> S = matrix_space(R, 4, 4)
Matrix space of 4 rows and 4 columns
  over univariate polynomial ring in x over integers

julia> M = S([-6*x^2+6*x+12 -12*x^2-21*x-15 -15*x^2+21*x+33 -21*x^2-9*x-9;
              -8*x^2+8*x+16 -16*x^2+38*x-20 90*x^2-82*x-44 60*x^2+54*x-34;
              -4*x^2+4*x+8 -8*x^2+13*x-10 35*x^2-31*x-14 22*x^2+21*x-15;
              -10*x^2+10*x+20 -20*x^2+70*x-25 150*x^2-140*x-85 105*x^2+90*x-50])
[  -6*x^2 + 6*x + 12   -12*x^2 - 21*x - 15    -15*x^2 + 21*x + 33     -21*x^2 - 9*x - 9]
[  -8*x^2 + 8*x + 16   -16*x^2 + 38*x - 20     90*x^2 - 82*x - 44    60*x^2 + 54*x - 34]
[   -4*x^2 + 4*x + 8    -8*x^2 + 13*x - 10     35*x^2 - 31*x - 14    22*x^2 + 21*x - 15]
[-10*x^2 + 10*x + 20   -20*x^2 + 70*x - 25   150*x^2 - 140*x - 85   105*x^2 + 90*x - 50]

julia> n, N = nullspace(M)
(2, [1320*x^4-330*x^2-1320*x-1320 1056*x^4+1254*x^3+1848*x^2-66*x-330; -660*x^4+1320*x^3+1188*x^2-1848*x-1056 -528*x^4+132*x^3+1584*x^2+660*x-264; 396*x^3-396*x^2-792*x 0; 0 396*x^3-396*x^2-792*x])
```

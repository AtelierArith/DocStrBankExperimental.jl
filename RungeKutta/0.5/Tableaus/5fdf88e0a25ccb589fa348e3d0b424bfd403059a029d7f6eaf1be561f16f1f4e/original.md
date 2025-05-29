Lobatto III tableau with s stages

```julia
TableauLobattoIII(::Type{T}, s)
TableauLobattoIII(s) = TableauLobattoIII(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

Sometimes this tableau is also referred to as Lobatto IIIC*.

References:

```
John C. Butcher.
Integration processes based on Radau quadrature formulas
Mathematics of Computation, Volume 18, Pages 233-244, 1964.
doi: 10.1090/S0025-5718-1964-0165693-1.

Laurent O. Jay.
Lobatto Methods.
In: Engquist B. (eds). Encyclopedia of Applied and Computational Mathematics. Springer, Berlin, Heidelberg. 2015.
doi: 10.1007/978-3-540-70529-1_123.
```

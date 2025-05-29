Lobatto IIIC tableau with s stages

```julia
TableauLobattoIIIC(::Type{T}, s)
TableauLobattoIIIC(s) = TableauLobattoIIIC(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

References:

```
F. H. Chipman.
A-stable Runge-Kutta processes.
BIT, Volume 11, Pages 384-388, 1971.
doi: 10.1007/BF01939406.

Laurent O. Jay.
Lobatto Methods.
In: Engquist B. (eds). Encyclopedia of Applied and Computational Mathematics. Springer, Berlin, Heidelberg. 2015.
doi: 10.1007/978-3-540-70529-1_123.
```

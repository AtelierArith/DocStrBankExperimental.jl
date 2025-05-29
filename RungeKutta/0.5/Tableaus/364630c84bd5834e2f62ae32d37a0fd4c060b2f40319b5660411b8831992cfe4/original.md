Lobatto IIIB tableau with s stages

```julia
TableauLobattoIIIB(::Type{T}, s)
TableauLobattoIIIB(s) = TableauLobattoIIIB(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

References:

```
Byron Leonard Ehle.
On Padé approximations to the exponential function and a-stable methods for the numerical solution of initial value problems.
Research Report CSRR 2010, Dept. AACS, University of Waterloo, 1969.

Laurent O. Jay.
Lobatto Methods.
In: Engquist B. (eds). Encyclopedia of Applied and Computational Mathematics. Springer, Berlin, Heidelberg. 2015.
doi: 10.1007/978-3-540-70529-1_123.
```

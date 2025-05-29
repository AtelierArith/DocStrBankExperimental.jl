`schur_functor(mat,l)`

`mat`  should be  a square  matrix and  `l` a  partition. The result is the Schur  functor  of  the  matrix  `mat`  corresponding to partition `l`; for example,   if  `l==[n]`  it  returns  the   n-th  symmetric  power  and  if `l==[1,1,1]` it returns the 3rd exterior power. The current algorithm (from Littlewood)  is rather inefficient so it is  quite slow for partitions of n where `n>6`.

```julia-repl
julia> m=cartan(:A,3)
3×3 Matrix{Int64}:
  2  -1   0
 -1   2  -1
  0  -1   2

julia> schur_functor(m,[2,2])
6×6 Matrix{Rational{Int64}}:
   9    -6    4   3    -2    1
 -12    16  -16  -8     8   -4
   4    -8   16   4    -8    4
 -3//2  -1    2  7//2  -3   5//2
  -4     8  -16  -8    16  -12
   1    -2    4   3    -6    9
```

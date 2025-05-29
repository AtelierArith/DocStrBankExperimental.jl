```
SafeRightDivide(B, A, L)
```

Returns: a homalg matrix

Same as RightDivide, but asserts that the result is not fail.

```jldoctest
julia> A = HomalgMatrix(1:9, 3, 3, ZZ)
[1   2   3]
[4   5   6]
[7   8   9]

julia> B = HomalgMatrix([3, 5, 7, 13, 16, 19, 29, 33, 37], 3, 3, ZZ)
[ 3    5    7]
[13   16   19]
[29   33   37]

julia> L = HomalgMatrix(2:10, 3, 3, ZZ)
[2   3    4]
[5   6    7]
[8   9   10]

julia> X = SafeRightDivide(B, A, L)
[0   0   -2]
[0   0   -1]
[0   0    0]

julia> Y = HomalgMatrix([1, 3, 0, 0, 4, 0, -3, 7, 0], 3, 3, ZZ)
[ 1   3   0]
[ 0   4   0]
[-3   7   0]

julia> X*A+Y*L
[ 3    5    7]
[13   16   19]
[29   33   37]

julia> B = HomalgMatrix([3, 5, 7, 0, 16, 19, 0, 33, 37], 3, 3, ZZ)
[3    5    7]
[0   16   19]
[0   33   37]

julia> SafeRightDivide(B, A, L)
ERROR: Unable to solve linear system
```

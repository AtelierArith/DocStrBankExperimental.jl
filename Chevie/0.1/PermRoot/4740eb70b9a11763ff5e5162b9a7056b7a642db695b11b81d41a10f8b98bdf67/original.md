`asreflection(s::Matrix [,r::AbstractVector])`

`s`  should be is a square  matrix, and if given `r`  should be a vector of length  `size(s,1)`.  The  function  determines  if  `s` is the matrix of a complex  reflection  (resp.  if  `r`  is  given  if  it  is the matrix of a reflection  of root `r`; the point of  giving `r` is to specify exactly the desired root and coroot, which otherwise are determined only up to a scalar and  its  inverse).  The  function  returns  `nothing`  if  `s` if is not a reflection  (resp. not a reflection with root `r`), and otherwise returns a named tuple with four fields:

`.root`:   the root of the reflection `s` (equal to `r` if given)

`.coroot`:  the coroot of `s`

`.eigenvalue`:  the non-trivial eigenvalue of `s`

`.isunitary`: a boolean which is `true` if and only if `s` is unitary   with  respect to the usual scalar product  (then `s` is determined by the   root and the eigenvalue as `reflectionMatrix(.root,.eigenvalue)`)

```julia-repl
julia> asreflection([-1 0 0;1 1 0;0 0 1])
(root = [2, 0, 0], coroot = Rational{Int64}[1, -1//2, 0], eig = -1, isunitary = false)

julia> asreflection([-1 0 0;1 1 0;0 0 1],[1,0,0])
(root = [1, 0, 0], coroot = Rational{Int64}[2, -1, 0], eig = -1, isunitary = false)
```

`reflectionMatrix(root,  coroot)` the matrix of the reflection with a given root and coroot.

A (complex) reflection is a finite order element `s` of `GL(V)`, the linear group of a vector space over a subfield of the complex numbers, whose fixed points  form  a  hyperplane  `H`  (the  *reflecting hyperplane* of `s`); an eigenvector  `r` for  the non-trivial  eigenvalue `ζ`  (a root of unity) is called  a *root* of `s`. If we choose  a linear form `rᵛ` defining `H` such that `rᵛ(r)=1-ζ` (a *coroot* of `s`) then `s` is given by `x↦ x-rᵛ(x)r`.

A  way  of  specifying  `s`  is  by  giving  a root and a coroot, which are uniquely determined by `s` up to multiplication of the root by a scalar and of  the coroot by the inverse scalar. The function `reflectionMatrix` gives the  matrix of the  corresponding reflection in  the standard basis of `V`, where  the `root` and the `coroot` are  vectors given in the standard bases of `V` and `Vᵛ`, so the pairing `rᵛ(r)` is obtained as `transpose(root)*coroot`.

```
julia> r=reflectionMatrix([1,0,0],[2,-1,0])
3×3 Matrix{Int64}:
 -1  0  0
  1  1  0
  0  0  1

julia> r==reflrep(coxgroup(:A,3),1)
true

julia> r*[2,-1,0]
3-element Vector{Int64}:
 -2
  1
  0

julia> [1 0 0]*r
1×3 Matrix{Int64}:
 -1  0  0
```

As  we see in the last lines, in  Julia a matrix operates from the right on the  vector space `V`  of row vectors  and from the  left on the dual space `Vᵛ` of column vectors.

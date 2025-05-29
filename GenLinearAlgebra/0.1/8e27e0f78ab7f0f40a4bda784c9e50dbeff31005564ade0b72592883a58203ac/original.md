`permanent(m)`

returns the *permanent* of the square matrix `m`, which is defined by  $\sum_{p\in\frak S_n}\prod_{i=1}^n m[i,p(i)]$.

Note the similarity of the definition of  the permanent to the definition of the determinant.  In  fact the only  difference is the missing sign of the permutation.  However the  permanent is quite unlike the determinant, for example   it is  not  multilinear or  alternating.  It   has  however important combinatorical properties.

```julia-repl
julia> permanent([0 1 1 1;1 0 1 1;1 1 0 1;1 1 1 0]) # inefficient way to compute the number of derangements of 1:4
9

julia> permanent([1 1 0 1 0 0 0; 0 1 1 0 1 0 0;0 0 1 1 0 1 0; 0 0 0 1 1 0 1;1 0 0 0 1 1 0;0 1 0 0 0 1 1;1 0 1 0 0 0 1]) # 24 permutations fit the projective plane of order 2 
24 
```

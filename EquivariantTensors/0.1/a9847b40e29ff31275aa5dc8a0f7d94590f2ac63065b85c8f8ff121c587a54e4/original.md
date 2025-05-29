`SparseSymmProd` : sparse symmetric product with entries stored as tuples.  Input is a vector `A`; each entry of the output vector `AA` is of the form 

$$
 {\bm A}_{i_1, \dots, i_N} = \prod_{t = 1}^N A_{i_t}.
$$

### Constructor

```julia
SparseSymmProd(spec)
```

where `spec` is a list of tuples or vectors, each of which specifies an `AA` basis function as described above. For example, 

```julia
spec = [ (1,), (2,), (1,1), (1,2), (2,2), 
         (1,1,1), (1,1,2), (1,2,2), (2,2,2) ]
basis = SparseSymmProd(spec)         
```

defines a basis of 9 functions, 

$$
[ A_1, A_2, A_1^2, A_1 A_2, A_2^2, A_1^3, A_1^2 A_2, A_1 A_2^2, A_2^3 ]
$$

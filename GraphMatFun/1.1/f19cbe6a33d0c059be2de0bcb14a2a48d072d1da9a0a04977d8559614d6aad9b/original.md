```
 (graph,crefs)=graph_exp_native_jl(A; input=:A)
```

Creates a graph for the native scaling-and-squaring for the matrix exponential, as implemented in Julia. The matrix `A` is taken as input to determine the length of the Padé approximant and the number of squares applied, as well as determining the type of the coefficients. The kwarg `input` determines the name of the matrix, in the graph.

**References**

1. N. J. Higham. "Functions of Matrices". SIAM, Philadelphia, PA, 2008. DOI: [10.1137/1.9780898717778](https://doi.org/10.1137/1.9780898717778)
2. N. J. Higham. "The Scaling and Squaring Method for the Matrix Exponential Revisited". SIAM Journal on Matrix Analysis and Applications, 26(4):1179-1193, 2005. DOI: [10.1137/04061101X](https://doi.org/10.1137/04061101X)
3. "Julia's matrix exponential", [at the time of conversion](https://github.com/JuliaLang/julia/blob/697e782ab86bfcdd7fd15550241fe162c51d9f98/stdlib/LinearAlgebra/src/dense.jl#L554).

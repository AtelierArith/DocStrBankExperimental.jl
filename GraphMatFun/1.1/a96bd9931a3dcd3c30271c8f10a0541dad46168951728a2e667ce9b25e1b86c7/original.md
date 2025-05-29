```
(graph,crefs)=graph_degopt(k;T=ComplexF64,input=:A)
(graph,crefs)=graph_degopt(x,z;input=:A)
(graph,crefs)=graph_degopt(d::Degopt;input=:A)
```

Corresponds to the (for a fixed number of multiplications) degree-optimal polynomial

```
B1=A
B2=(x *I+x *A)(x *I+x *A)
B3=(x *I+x *A+x*B2)(x *I+x *A+x *B2)
 ..
```

and

```
Out=z*I+z*A1+z*B2+z*B3+z*B4...
```

The `x`-values are given in the argument `x`, which is a `Vector{Tuple{Vector,Vector}}`, containing the elements of each sum. The `z`-vector contains the elements to form the output, and `input` determines the name of the matrix A above. If the parameter `k` is supplied instead of the coefficients, all coeffs will be set to one. The general recursion is given in (9) in the paper referenced below.

**Reference**

1. P. Bader, S. Blanes, and F. Casas, "Computing the matrix exponential with an optimized Taylor polynomial approximation", Mathematics, 7(12), 2019. DOI: [10.3390/math7121174](https://doi.org/10.3390/math7121174)

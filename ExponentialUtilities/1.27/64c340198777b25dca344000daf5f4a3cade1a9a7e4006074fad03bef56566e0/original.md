```
arnoldi(A,b[;m,tol,opnorm,iop]) -> Ks
```

Performs `m` arnoldi iterations to obtain the Krylov subspace K_m(A,b).

The n x (m + 1) basis vectors `getV(Ks)` and the (m + 1) x m upper Hessenberg matrix `getH(Ks)` are related by the recurrence formula

```
v_1=b,\quad Av_j = \sum_{i=1}^{j+1}h_{ij}v_i\quad(j = 1,2,\ldots,m)
```

`iop` determines the length of the incomplete orthogonalization procedure [^1]. The default value of 0 indicates full Arnoldi. For symmetric/Hermitian `A`, `iop` will be ignored and the Lanczos algorithm will be used instead.

Refer to `KrylovSubspace` for more information regarding the output.

Happy-breakdown occurs whenever `norm(v_j) < tol * opnorm`, in this case, the dimension of `Ks` is smaller than `m`.

[^1]: Koskela, A. (2015). Approximating the matrix exponential of an advection-diffusion operator using the incomplete orthogonalization method. In Numerical Mathematics and Advanced Applications-ENUMATH 2013 (pp. 345-353). Springer, Cham.

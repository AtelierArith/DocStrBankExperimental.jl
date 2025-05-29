```
chbv(A, vec)
```

Calculate matrix exponential acting on some vector using the Chebyshev method.

# Input

  * `A`   – matrix which can be dense or sparse
  * `vec` – vector on which the matrix exponential of `A` is applied

# Notes

This Julia implementation is based on Expokit's CHBV Matlab code by Roger B. Sidje, see below.

---

```
y = chbv( H, x )
CHBV computes the direct action of the matrix exponential on
a vector: y = exp(H) * x. It uses the partial fraction expansion of
the uniform rational Chebyshev approximation of type (14,14).
About 14-digit accuracy is expected if the matrix H is symmetric
negative definite. The algorithm may behave poorly otherwise.
See also PADM, EXPOKIT.

Roger B. Sidje (rbs@maths.uq.edu.au)
EXPOKIT: Software Package for Computing Matrix Exponentials.
ACM - Transactions On Mathematical Software, 24(1):130-156, 1998
```

```
padm(A; p=6)
```

Calculate matrix exponential using Pade approximants.

`padm` uses the irreducible (p, p)-degree rational Pade approximation to the exponential function. The result is always a dense matrix.

# Input

  * `A` – matrix which can be dense or sparse
  * `p` – (optional, default: 6) degree of the rational Pade approximation to        the exponential function

# Notes

This Julia implementation originated from Expokit's PADM Matlab code by Roger B. Sidje, see below.

---

E = padm( A, p )   PADM computes the matrix exponential exp(A) using the irreducible    (p,p)-degree rational Pade approximation to the exponential function.

E = padm( A )   p is internally set to 6 (recommended and generally satisfactory).

See also CHBV, EXPOKIT and the MATLAB supplied functions EXPM and EXPM1.

Roger B. Sidje (rbs@maths.uq.edu.au)   EXPOKIT: Software Package for Computing Matrix Exponentials.   ACM - Transactions On Mathematical Software, 24(1):130-156, 1998

```
B = elementary_divisors(A)
```

Computes the Smith normal form of `A`, `B=SAT` returning the elementary divisors, the diagonal of `B`.

The matrices `S,B,T` are integer matrices with

  * |det(S)| = |det(T)| = 1 such that B = SAT
  * B is a diagonal matrix
  * B[i,i] >= 0 for all i
  * B[i,i] divides all B[j,j] for all j > i

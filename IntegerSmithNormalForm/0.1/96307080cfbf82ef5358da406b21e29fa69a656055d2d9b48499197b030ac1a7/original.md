```
(S,B,T) = snf!(A)
```

Computes the Smith normal form `B = SAT`, where `B` is computed inplace of `A`.

The matrices `S,B,T` are integer matrices with

  * |det(S)| = |det(T)| = 1 such that B = SAT
  * B is a diagonal matrix
  * B[i,i] >= 0 for all i
  * B[i,i] divides all B[j,j] for all j > i

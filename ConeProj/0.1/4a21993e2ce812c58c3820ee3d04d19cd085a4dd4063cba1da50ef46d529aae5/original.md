Add a column to a QR factorization without using Q.

`R = qraddcol(A,R,v)`  adds the m-vector `v` to the QR factorization of the m-by-n matrix `A` without using `Q`. On entry, `R` is a dense n-by-n upper triangular matrix such that `R'*R = A'*A`.

`R = qraddcol(A,R,v,β)` is similar to the above, except that the routine updates the QR factorization of

[A; β I],   and   R'*R = (A'*A + β^2*I) = R'*R.

`A` should have fewer columns than rows.  `A` and `v` may be sparse or dense.  On exit, `R` is the (n+1)-by-(n+1) factor corresponding to

Anew = [A        V ],    Rnew = [R   u  ],   Rnew'Rnew = Anew'Anew.          [beta*I     ]            [  gamma]          [       beta]

The new column `v` is assumed to be nonzero. If `A` has no columns yet, input `A = []`, `R = []`.

```
15 Jun 2007: First version of QRaddcol.m (without beta).
             Michael Friedlander (mpf@cs.ubc.ca) and
             Michael Saunders (saunders@stanford.edu)
             Where necessary, Ake Bjorck's CSNE
             (Corrected Semi-Normal Equations) method
             is used to improve the accuracy of u and gamma.
             See p143 of Ake Bjork's Least Squares book.
18 Jun 2007: R is now the exact size on entry and exit.
19 Oct 2007: Sparse A, a makes c and u sparse.
             Force them to be dense.
             For dense R we probably should use linsolve,
             which requires c and u to be dense anyway.
04 Aug 2008: QRaddcol2 updates u using du, rather than
             u = R*z as in Ake's book.
             We guess that it might be slightly more accurate,
             but it's hard to tell.  No R*z makes it a little cheaper.
03 Sep 2008: Generalize A to be [A; beta*I] for some scalar beta.
             Update u using du, but keep Ake's version in comments.
29 Dec 2015: Converted to Julia.
```

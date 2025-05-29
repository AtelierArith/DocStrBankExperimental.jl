Delete the k-th column and update a Q-less QR factorization.

`R = qrdelcol(R,k)` deletes the k-th column of the upper-triangular `R` and restores it to upper-triangular form.  On input, `R` is an n x n upper-triangular matrix.  On output, `R` is an n-1 x n-1 upper triangle.

```
18 Jun 2007: First version of QRdelcol.m.
             Michael Friedlander (mpf@cs.ubc.ca) and
             Michael Saunders (saunders@stanford.edu)
             To allow for R being sparse,
             we eliminate the k-th row of the usual
             Hessenberg matrix rather than its subdiagonals,
             as in Reid's Bartel-Golub LU update and also
             the Forrest-Tomlin update.
             (But Matlab will still be pretty inefficient.)
18 Jun 2007: R is now the exact size on entry and exit.
30 Dec 2015: Translate to Julia.
```

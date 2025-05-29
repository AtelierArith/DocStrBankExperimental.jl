Fast implementation of the AZ Algorithm. Returns an operator that is approximately `pinv(A)`, based on a suitable `Zt` so that `(A*Zt-I)*A` is low rank.

Steps when applying to right hand side b:

1. (I-A*Zt)*A*x2=(I-A*Zt)*b, solve for x2

This is by default done using a low rank decomposition of (I-A*Zt)*A (RandomizedSvdSolver).

2. x1 = Zt*(b-A*x2)

Can be done fast if Zt and A are fast.

3. x = x1+x2

This is the solution.

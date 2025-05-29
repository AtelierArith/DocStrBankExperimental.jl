Estimates the norms ||Q||, ||Q^2||, ... ||Q^m|| on U^0.

U is the matrix [ones(1,n-1); -I_(n-1,n-1)]. It is currently assumed that f*U==0 (i.e., all elements of f are equal).

f must be an interval vector.

The following constants may be specified as keyword arguments:

normQ, normE, normv0, normEF, normIEF, normN

otherwise they are computed (which may be slower).

e and f must be specified in case is*integral*preserving==false In case is*integral*preserving is true, they may be specified but they are then ignored.

Implementation note: currently we perform this computation one column at a time, to be able to scale (slowly) to cases with large size; for moderate sizes, it would indeed be better to do the computation all columns at the same time, in BLAS level 3.

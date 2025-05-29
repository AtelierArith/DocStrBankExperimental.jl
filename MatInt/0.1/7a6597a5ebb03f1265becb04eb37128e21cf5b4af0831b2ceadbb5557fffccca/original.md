This  package  provides  the  Smith  and  Hermite normal forms for integral matrices,  the Diaconis-Graham  normal form  for sets  of generators  of an abelian  group,  and  a  few  functions to  work  with integral matrices as lattices.

Most  of the  code is  ported from  `GAP4`, authored  by A.  Storjohann, R. Wainwright, F. Gähler and D. Holt; the code for `NormalFormIntMat` is still hard  to read  like the  original one.  The Diaconis-Graham  normal form is ported from `GAP3/Chevie`.

The  best way to make sure  of the validity of the  results is to work with matrices of `SaferIntegers`, which error in case of overflow. Then redo the computation with a wider type in case of error.

For  the API, look at the docstrings for `smith, smith_transforms, hermite, hermite_transforms,  col_hermite,  col_hermite_transforms, diaconis_graham, baseInt, complementInt, lnullspaceInt, solutionmatInt, intersect_rowspaceInt`. 

We  recall  that  a  *unimodular*  matrix  means an integer matrix which is invertible and whose inverse is still an integer matrix.

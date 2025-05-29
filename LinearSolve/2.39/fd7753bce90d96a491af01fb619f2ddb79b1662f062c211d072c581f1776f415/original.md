`SparspakFactorization(reuse_symbolic = true)`

This is the translation of the well-known sparse matrix software Sparspak (Waterloo Sparse Matrix Package), solving large sparse systems of linear algebraic equations. Sparspak is composed of the subroutines from the book "Computer Solution of Large Sparse Positive Definite Systems" by Alan George and Joseph Liu. Originally written in Fortran 77, later rewritten in Fortran 90. Here is the software translated into Julia.

The Julia rewrite is released  under the MIT license with an express permission from the authors of the Fortran package. The package uses multiple dispatch to route around standard BLAS routines in the case e.g. of arbitrary-precision floating point numbers or ForwardDiff.Dual. This e.g. allows for Automatic Differentiation (AD) of a sparse-matrix solve.

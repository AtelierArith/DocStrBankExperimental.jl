```
floquet = FloquetQaD(eigsolver::AbstractEigenSolver, matrix_free = ~(eigls isa AbstractDirectEigenSolver)
```

This composite type implements the computation of the eigenvalues of the monodromy matrix in the case of periodic orbits problems (based on the Shooting method or Finite Differences (Trapeze method)), also called the Floquet multipliers. The method, dubbed Quick and Dirty (QaD), is not numerically very precise for large / small Floquet exponents when the number of time sections is large because of many matrix products. It allows, nevertheless, to detect bifurcations. The arguments are as follows:

  * `eigsolver::AbstractEigenSolver` solver used to compute the eigenvalues.
  * `matrix_free::Bool` whether to use matrix-free linear operator

If `eigsolver == DefaultEig()`, then the monodromy matrix is formed and its eigenvalues are computed. Otherwise, a Matrix-Free version of the monodromy is used.

!!! danger "Floquet multipliers computation"
    The computation of Floquet multipliers is necessary for the detection of bifurcations of periodic orbits (which is done by analyzing the Floquet exponents obtained from the Floquet multipliers). Hence, the eigensolver `eigsolver` needs to compute the eigenvalues with largest modulus (and not with largest real part which is their default behavior). This can be done by changing the option `which = :LM` of `eigsolver`. Nevertheless, note that for most implemented eigensolvers in the current Package, the proper option is set.


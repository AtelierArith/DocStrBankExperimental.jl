```
function dsvd(A::AbstractMultipliableMatrix,Prange::UnitSymmetricMatrix,Pdomain::UnitSymmetricMatrix;full=false,alg::LinearAlgebra.Algorithm = LinearAlgebra.default_svd_alg(A.numbers)) 

Dimensioned singular value decomposition (DSVD).
Appropriate version of SVD for non-uniform matrices.
`svd` can be computed for `Number`s, `Adjoint`s, `Transpose`s, and `Integers`; `dsvd` doesn't yet implement these.
```

# Input

  * `A::AbstractMultipliableMatrix`
  * `Pr::UnitSymmetricMatrix`: square matrix defining norm of range
  * `Pd::UnitSymmetricMatrix`: square matrix defining norm of domain
  * `full=false`: optional argument
  * `alg`: optional argument for algorithm

# Output:

  * `F::DSVD`: Dimensioned SVD object with units that can be deconstructed

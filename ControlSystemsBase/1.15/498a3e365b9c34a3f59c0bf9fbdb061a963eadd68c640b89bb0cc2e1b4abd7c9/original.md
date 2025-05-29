```
tzeros(sys)
tzeros(sys::AbstractStateSpace; extra=Val(false))
```

Compute the invariant zeros of the system `sys`. If `sys` is a minimal realization, these are also the transmission zeros.

If `sys` is a state-space system the function has additional keyword arguments, see [`?ControlSystemsBase.MatrixPencils.spzeros`](https://andreasvarga.github.io/MatrixPencils.jl/dev/sklfapps.html#MatrixPencils.spzeros) for more details. If `extra = Val(true)`, the function returns `z, iz, KRInfo` where `z` are the transmission zeros, information on the multiplicities of infinite zeros in `iz` and information on the Kronecker-structure in the KRInfo object. The number of infinite zeros is the sum of the components of iz.

To compute zeros of a system with non-BLAS floats, such as `BigFloat`, install and load the package `GenericSchur.jl` before calling `tzeros`.

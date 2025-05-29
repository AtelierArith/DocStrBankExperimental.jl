```
metricmatrix(Vs::AbstractBasis)
```

Return the (real, symmetric) metric matrix of a basis `Vs`, i.e., the matrix with elements $G_{ij} =$ `dot(Vs[i], Vs[j])`, as defined in the International Tables of Crystallography, Volume A, Section 5.2.2.3.

Equivalently, this is the Gram matrix of `Vs`, and so can also be expressed as `Vm' * Vm` with `Vm` denoting the columnwise concatenation of the basis vectors in `Vs`.

See also [`volume`](@ref).

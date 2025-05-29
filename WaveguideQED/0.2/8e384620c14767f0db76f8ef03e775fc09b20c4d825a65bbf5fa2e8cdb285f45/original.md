```
WaveguideTransform{B1,B2,Np,idx} <: WaveguideOperator{B1,B2}
```

Operator structure for transforming an output state $\ket{\psi}_{\mathrm{out}} = \mathbf{C} \ket{\tilde{\psi}}_{\mathrm{out}}$ Np is used to dispatch one or two photon routine and idx denotes the index of the waveguide the operator is acting on. See also [`effective_hamiltonian`](@ref).

Examples:

```
times = 0:0.1:10
bw = WaveguideBasis(1,2,times)
C = 1/sqrt(2)*[1.0 -im;-im 1]
C_transform = WaveguideTransform(bw,C)
psi_tilde = ket(bw)
psi = C_transform*psi_tilde
```

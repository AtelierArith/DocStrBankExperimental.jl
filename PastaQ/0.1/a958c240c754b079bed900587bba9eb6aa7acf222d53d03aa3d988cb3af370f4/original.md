```
runcircuit(hilbert::Vector{<:Index}, circuit::Vector;
           full_representation::Bool = false,
           process::Bool = false,
           noise = nothing,
           kwargs...)

runcircuit(M::Union{MPS, MPO, ITensor}, circuit::Union{Tuple, AbstractVector};
           full_representation::Bool = false, noise = nothing, kwargs...)
```

Run the circuit corresponding to a list of quantum gates on a system of $n$ qubits, with input Hilbert space `hilbert`. The specific method of this general function is specified by the keyword arguments `process` and `noise`.

By default (`process = false` and `noise = nothing`), `runcircuit` returns an MPS wavefunction corresponding to the contraction of each quantum gate in `circuit` with the zero product state

$$
|\psi\rangle = U_M\dots U_2 U_1|0,0,\dots,0\rangle
$$

If `process = true`, the output is the MPO corresponding to the full unitary circuit:

$$
U = U_M\dots U_2 U_1
$$

If `noise` is set to a given input noise model (in lazy representation), Kraus operators are added to each gate in the circuit, and the output is the MPO density operator given by the contraction of the noisy circuit with input zero state:

$$
\rho = \mathcal{E}(|0,\dots,0\rangle\langle0,\dots,0|)
$$

Finally, if both `noise = ...` and `proces  = true`, the output is the full quantum channel, which we by default represent with its Choi matrix:

$$
\Lambda = (1+\mathcal{E})|\Phi\rangle\langle\Phi|^{\otimes n}
$$

If `full_representation = true`, the contraction is performed without approximation, leading to an output object whose size scales exponentiall with $n$

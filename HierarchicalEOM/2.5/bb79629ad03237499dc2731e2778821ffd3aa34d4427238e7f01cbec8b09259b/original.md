```
M_S(Hsys, parity=EVEN; verbose=true)
```

Generate HEOM Liouvillian superoperator matrix with cutoff level of the hierarchy equals to `0`.   This corresponds to the standard Schrodinger (Liouville-von Neumann) equation, namely

$$
M[\cdot]=-i \left[H_{sys}, \cdot \right]_-,
$$

where $[\cdot, \cdot]_-$ stands for commutator.

# Parameters

  * `Hsys` : The time-independent system Hamiltonian or Liouvillian
  * `parity::AbstractParity` : the parity label of the operator which HEOMLS is acting on (usually `EVEN`, only set as `ODD` for calculating spectrum of fermionic system).
  * `verbose::Bool` : To display verbose output during the process or not. Defaults to `true`.

Note that the parity only need to be set as `ODD` when the system contains fermionic systems and you need to calculate the spectrum (density of states) of it.

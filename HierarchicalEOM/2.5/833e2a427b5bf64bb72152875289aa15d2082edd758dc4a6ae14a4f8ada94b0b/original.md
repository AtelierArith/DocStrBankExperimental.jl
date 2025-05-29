```
addFermionDissipator(M, jumpOP)
```

Adding fermionic dissipator to a given HEOMLS matrix which describes how the system dissipatively interacts with an extra fermionic environment.   The dissipator with `EVEN` parity is defined as follows

$$
D_{\textrm{even}}[J](\cdot) = J(\cdot) J^\dagger - \frac{1}{2}\left(J^\dagger J (\cdot) + (\cdot) J^\dagger J \right),
$$

where $J\equiv \sqrt{\gamma}V$ is the jump operator, $V$ describes the dissipative part (operator) of the dynamics, $\gamma$ represents a non-negative damping rate and $[\cdot, \cdot]_+$ stands for anti-commutator.

Similarly, the dissipator with `ODD` parity is defined as follows

$$
D_{\textrm{odd}}[J](\cdot) = - J(\cdot) J^\dagger - \frac{1}{2}\left(J^\dagger J (\cdot) + (\cdot) J^\dagger J \right),
$$

Note that the parity of the dissipator will be determined by the parity of the given HEOMLS matrix `M`.

# Parameters

  * `M::AbstractHEOMLSMatrix` : the matrix given from HEOM model
  * `jumpOP::AbstractVector` : The list of collapse (jump) operators to add. Defaults to empty vector `[]`.

# Return

  * `M_new::AbstractHEOMLSMatrix` : the new HEOM Liouvillian superoperator matrix

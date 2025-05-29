```
addBosonDissipator(M, jumpOP)
```

Adding bosonic dissipator to a given HEOMLS matrix which describes how the system dissipatively interacts with an extra bosonic environment.   The dissipator is defined as follows

$$
D[J](\cdot) = J(\cdot) J^\dagger - \frac{1}{2}\left(J^\dagger J (\cdot) + (\cdot) J^\dagger J \right),
$$

where $J\equiv \sqrt{\gamma}V$ is the jump operator, $V$ describes the dissipative part (operator) of the dynamics, $\gamma$ represents a non-negative damping rate and $[\cdot, \cdot]_+$ stands for anti-commutator.

Note that if $V$ is acting on fermionic systems, it should be even-parity to be compatible with charge conservation.

# Parameters

  * `M::AbstractHEOMLSMatrix` : the matrix given from HEOM model
  * `jumpOP::AbstractVector` : The list of collapse (jump) operators $\{J_i\}_i$ to add. Defaults to empty vector `[]`.

# Return

  * `M_new::AbstractHEOMLSMatrix` : the new HEOM Liouvillian superoperator matrix

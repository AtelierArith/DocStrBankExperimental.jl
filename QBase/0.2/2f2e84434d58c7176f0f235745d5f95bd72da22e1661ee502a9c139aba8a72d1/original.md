```
mirror_symmetric_qubit_kets( θ :: Real ) :: Vector{Ket{Float64}}
```

Returns the triplet of qubit kets in the x-z plane of bloch sphere. The first ket is  $|0\rangle$ and the other two are symmetric across the z-axis, $|\pm\rangle = \cos(\theta)|0 \rangle \pm \sin(\theta)|1\rangle$.

Input:

  * `θ ∈ [0,π/2]`: the hilbert space angle between $|0\rangle$ and symmetric kets.

```
amplitude(dc::DecayChain, orientation_angles::PlaneOrientation, σs::MandelstamTuple; kw...)
```

Compute the amplitude for a given decay chain with orientation angles applied to the rotation of the final state.

# Arguments

  * `dc::DecayChain`: The decay chain object containing the system's configuration (e.g., spin, parity, etc.).
  * `orientation_angles::PlaneOrientation`: Named tuple representing the plane orientation angles (`α`, `cosβ`, `γ`) for the final state.
  * `σs::MandelstamTuple`: Tuple representing the Mandelstam variables that describe the kinematic invariants of the process.
  * `kw...`: Additional keyword arguments to be passed to the underlying `amplitude` calculation (e.g `refζs` reference kinematics).

# Returns

  * A four dimensional amplitude array

# Details

The function first computes the array of aligned amplitudes. Then it contract it with a Wigner D-matrix.

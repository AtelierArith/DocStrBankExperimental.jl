```
amplitude(dc::DecayChain, σs::MandelstamTuple, two_λs; refζs = (1, 2, 3, 1))
```

Compute the total amplitude for a given decay chain and kinematic configuration.

# Arguments

  * `dc::DecayChain`: The decay-chain object.
  * `σs::MandelstamTuple`: Tuple representing Mandelstam variables that describe the kinematic invariants of the process.
  * `two_λs`: A collection of helicity values for the particles involved in the decay.
  * `refζs`: Reference ζ indices for alignment rotations (default is `(1, 2, 3, 1)`).

# Returns

  * A four-dimensional array of amplitude values.

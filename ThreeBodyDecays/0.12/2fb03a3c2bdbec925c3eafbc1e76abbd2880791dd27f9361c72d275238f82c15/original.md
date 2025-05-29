```
amplitude(dc::DecayChain, σs::MandelstamTuple, two_λs; refζs = (1, 2, 3, 1))
```

Compute the total amplitude for a given decay chain, kinematic configuration, and all possible helicity values.

# Arguments

  * `dc::DecayChain`: The decay-chain object.
  * `σs::MandelstamTuple`: Tuple representing Mandelstam variables that describe the kinematic invariants of the process.
  * `refζs`: Reference ζ indices for alignment rotations (default is `(1, 2, 3, 1)`).

# Returns

  * A four-dimensional array of amplitude values.

```
read_final_state_particles(fname; maxevents = -1, skipevents = 0, T=PseudoJet)
```

Reads final state particles from a file and returns them as a vector of type T.

# Arguments

  * `fname`: The name of the HepMC3 ASCII file to read particles from. If the file is gzipped, the function will automatically decompress it.
  * `maxevents=-1`: The maximum number of events to read. -1 means all events will be read.
  * `skipevents=0`: The number of events to skip before an event is included.
  * `T=PseudoJet`: The type of object to construct and return.

# Returns

A vector of vectors of T objects, where each inner vector represents all the particles of a particular event. In particular T can be `PseudoJet` or a `LorentzVector` type. Note, if T is not `PseudoJet`, the order of the arguments in the constructor must be `(t, x, y, z)`.

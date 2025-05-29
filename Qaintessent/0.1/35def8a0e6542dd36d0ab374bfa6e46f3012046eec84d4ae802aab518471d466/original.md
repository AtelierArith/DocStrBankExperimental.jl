```
CircuitGate{M,G}(iwire::NTuple{M,<:Integer}, gate::G) where {M,G}
```

Creates a `CircuitGate{M,G}` object. `M` is the number of wires affected by the CircuitGate, and `G` is the basic gate used to construct the CircuitGate.

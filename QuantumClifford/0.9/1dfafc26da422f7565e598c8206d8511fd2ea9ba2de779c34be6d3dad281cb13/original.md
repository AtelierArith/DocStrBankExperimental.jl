Get the phase of the product of two Pauli operators.

Phase is encoded as F(4) in the low qubits of an UInt8.

```jldoctest
julia> P"ZZZ"*P"XXX"
-iYYY

julia> prodphase(P"ZZZ", P"XXX")
0x03

julia> prodphase(P"XXX", P"ZZZ")
0x01
```

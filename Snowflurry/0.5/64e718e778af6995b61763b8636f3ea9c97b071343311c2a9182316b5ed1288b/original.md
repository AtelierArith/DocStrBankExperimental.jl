```
Readout <: AbstractInstruction
```

`Readout` is an implementation of an `AbstractInstruction` that specifies  an explicit measurement on a particular qubit, and the destination bit in  the classical result registry (classical bit). It is built using the `readout(qubit::Int, bit::Int)` helper function, where  the first argument is the target qubit, and the second is the destination classical bit. Measurements are always performed in the $Z$ basis (also known as the computational basis).

# Examples

```jldoctest
julia> r = readout(1, 2)
Explicit Readout object:
   connected_qubit: 1 
   destination_bit: 2 

```

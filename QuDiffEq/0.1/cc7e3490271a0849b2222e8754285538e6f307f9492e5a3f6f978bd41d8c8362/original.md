```
HHLCRot{N, NC} <: PrimitiveBlock{N}
```

Controlled rotation gate used in HHL algorithm, applied on N qubits.

```
* cbits: control bits.
* ibit:: the ancilla bit.
* C_value:: the value of constant "C", should be smaller than the spectrum "gap".
```

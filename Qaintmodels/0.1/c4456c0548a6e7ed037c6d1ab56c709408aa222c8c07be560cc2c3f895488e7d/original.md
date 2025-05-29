```
vbe_adder_circuit(N)
```

Construct an in-place adder for 2 integers represented by `N` qubits. Based on ripple-carry adder circuit in Vedral et. al (Phys. Rev. A 54, 147 (1996), arXiv:quant-ph/9511018) Returns a CircuitGateChain{3N+1} as there are N+1 ancillary wires

If the two added integers are represented as:

$A = a_{0}\times 2^{0} + a_{1} \times 2^{1} + a_{2} \times 2^{2} + .. + a_{N} \times 2^{N} \\ B = b_{0}\times 2^{0} + b_{1} \times 2^{1} + b_{2} \times 2^{2} + .. + b_{N} \times 2^{N}$

The input index should be $a_{0}a_{1}a_{2}..a_{N}b_{0}b_{1}b_{2}..b_{N} + 1$ with $a_{0}$ as the fastest running index

The output index will be in the form $a_{0}a_{1}a_{2}..a_{N}c_{0}c_{1}c_{2}..c_{N} + 1$ where:

$C = (A+B) \% (2^{N} + 1) = c_{0}\times 2^{0} + c_{1} \times 2^{1} + c_{2} \times 2^{2} + ... + c_{N} \times 2^{N}$

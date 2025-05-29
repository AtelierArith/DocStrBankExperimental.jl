Random brickwork Clifford circuit.

The connectivity of the random circuit is brickwork in some dimensions. Each gate in the circuit is a random 2-qubit Clifford gate.

The brickwork is defined as follows: The qubits are arranged as a lattice, and `lattice_size` contains side length in each dimension. For example, a chain of length five will have `lattice_size = (5,)`, and a 5×5 lattice will have `lattice_size = (5, 5)`.

In multi-dimensional cases, gate layers act alternatively along each direction. The nearest two layers along the same direction are offset by one qubit, forming a so-called brickwork. The boundary condition is chosen as open.

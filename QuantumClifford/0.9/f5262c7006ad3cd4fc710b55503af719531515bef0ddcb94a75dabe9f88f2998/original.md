Get bipartite entanglement entropy of a subsystem

Defined as entropy of the reduced density matrix.

It can be calculated with multiple different algorithms, the most performant one depending on the particular case.

Currently implemented are the `:clip` (clipped gauge), `:graph` (graph state), and `:rref` (Gaussian elimination) algorithms. Benchmark your particular case to choose the best one.

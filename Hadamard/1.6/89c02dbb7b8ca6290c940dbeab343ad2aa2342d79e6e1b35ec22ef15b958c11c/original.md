The `Hadamard` module provides functions to compute fast Walsh-Hadamard transforms in Julia, for arbitrary dimensions and arbitrary power-of-two transform sizes, with the three standard orderings: natural (Hadamard), dyadic (Paley), and sequency (Walsh) ordering. See the `fwht`, `fwht_natural`, and `fwht_dyadic` functions, along with their inverses `ifwht` etc.

There is also a function `hadamard(n)` that returns Hadamard matrices for known sizes (including non powers of two).

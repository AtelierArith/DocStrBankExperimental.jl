```
root_lattice_recognition_fundamental(L::ZZLat)
```

Return the ADE type of the root sublattice of `L` as well as the corresponding irreducible root sublattices with basis given by a fundamental root system.

The type `(:I, 1)` corresponds to the odd unimodular root lattice of rank 1.

Input:

`L` – a definite and integral $\mathbb Z$-lattice.

Output:

  * the root sublattice, with basis given by a fundamental root system
  * the ADE types
  * a Vector consisting of the irreducible root sublattices.

# Examples

```jldoctest
julia> L = integer_lattice(gram=ZZ[4  0 0  0 3  0 3  0;
                            0 16 8 12 2 12 6 10;
                            0  8 8  6 2  8 4  5;
                            0 12 6 10 2  9 5  8;
                            3  2 2  2 4  2 4  2;
                            0 12 8  9 2 12 6  9;
                            3  6 4  5 4  6 6  5;
                            0 10 5  8 2  9 5  8])
Integer lattice of rank 8 and degree 8
with gram matrix
[4    0   0    0   3    0   3    0]
[0   16   8   12   2   12   6   10]
[0    8   8    6   2    8   4    5]
[0   12   6   10   2    9   5    8]
[3    2   2    2   4    2   4    2]
[0   12   8    9   2   12   6    9]
[3    6   4    5   4    6   6    5]
[0   10   5    8   2    9   5    8]

julia> R = root_lattice_recognition_fundamental(L);

julia> gram_matrix(R[1])
[2    0    0    0    0    0    0]
[0    2    0   -1    0    0    0]
[0    0    2   -1    0    0    0]
[0   -1   -1    2   -1    0    0]
[0    0    0   -1    2   -1    0]
[0    0    0    0   -1    2   -1]
[0    0    0    0    0   -1    2]

```

```
root_lattice_recognition(L::ZZLat)
```

Return the ADE type of the root sublattice of `L`.

The root sublattice is the lattice spanned by the vectors of squared length $1$ and $2$.  The odd lattice of rank 1 and determinant $1$ is denoted by `(:I, 1)`.

Input:

`L` – a definite and integral $\mathbb{Z}$-lattice.

Output:

Two lists, the first one containing the ADE types and the second one the irreducible root sublattices.

For more recognizable gram matrices use [`root_lattice_recognition_fundamental`](@ref).

# Examples

```jldoctest
julia> L = integer_lattice(; gram=ZZ[4  0 0  0 3  0 3  0;
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

julia> R = root_lattice_recognition(L)
([(:A, 1), (:D, 6)], ZZLat[Integer lattice of rank 1 and degree 8, Integer lattice of rank 6 and degree 8])

julia> L = integer_lattice(; gram = QQ[1 0 0  0;
                                       0 9 3  3;
                                       0 3 2  1;
                                       0 3 1 11])
Integer lattice of rank 4 and degree 4
with gram matrix
[1   0   0    0]
[0   9   3    3]
[0   3   2    1]
[0   3   1   11]

julia> root_lattice_recognition(L)
([(:A, 1), (:I, 1)], ZZLat[Integer lattice of rank 1 and degree 4, Integer lattice of rank 1 and degree 4])
```

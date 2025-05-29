```
hyperkaehler_lattice(S::Symbol; n::Int = 2)
```

Return the integer lattice corresponding to the Beauville-Bogomolov-Fujiki form on a hyperkaehler manifold whose deformation type is determined by `S` and `n`.

  * If `S == :K3` or `S == :Kum`, then `n` must be an integer bigger than 2;
  * If `S == :OG6` or `S == :OG10`, the value of `n` has no effect.

# Examples

```jldoctest
julia> L = hyperkaehler_lattice(:Kum; n = 3)
Integer lattice of rank 7 and degree 7
with gram matrix
[0   1   0   0   0   0    0]
[1   0   0   0   0   0    0]
[0   0   0   1   0   0    0]
[0   0   1   0   0   0    0]
[0   0   0   0   0   1    0]
[0   0   0   0   1   0    0]
[0   0   0   0   0   0   -8]

julia> L = hyperkaehler_lattice(:OG6)
Integer lattice of rank 8 and degree 8
with gram matrix
[0   1   0   0   0   0    0    0]
[1   0   0   0   0   0    0    0]
[0   0   0   1   0   0    0    0]
[0   0   1   0   0   0    0    0]
[0   0   0   0   0   1    0    0]
[0   0   0   0   1   0    0    0]
[0   0   0   0   0   0   -2    0]
[0   0   0   0   0   0    0   -2]

julia> L = hyperkaehler_lattice(:OG10);

julia> genus(L)
Genus symbol for integer lattices
Signatures: (3, 0, 21)
Local symbols:
  Local genus symbol at 2: 1^-24
  Local genus symbol at 3: 1^-23 3^1

julia> L = hyperkaehler_lattice(:K3; n = 3);

julia> genus(L)
Genus symbol for integer lattices
Signatures: (3, 0, 20)
Local symbol:
  Local genus symbol at 2: 1^22 4^1_7
```

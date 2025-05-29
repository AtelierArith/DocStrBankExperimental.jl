```
mukai_lattice(S::Symbol = :K3; extended::Bool = false)
```

Return the (extended) Mukai lattice.

If `S == :K3`, it returns the (extended) Mukai lattice associated to hyperkaehler manifolds which are deformation equivalent to a moduli space of stable sheaves on a K3 surface.

If `S == :Ab`, it returns the (extended) Mukai lattice associated to hyperkaehler manifolds which are deformation equivalent to a moduli space of stable sheaves on an abelian surface.

# Examples

```jldoctest
julia> L = mukai_lattice();

julia> genus(L)
Genus symbol for integer lattices
Signatures: (4, 0, 20)
Local symbol:
  Local genus symbol at 2: 1^24

julia> L = mukai_lattice(; extended = true);

julia> genus(L)
Genus symbol for integer lattices
Signatures: (5, 0, 21)
Local symbol:
  Local genus symbol at 2: 1^26

julia> L = mukai_lattice(:Ab);

julia> genus(L)
Genus symbol for integer lattices
Signatures: (4, 0, 4)
Local symbol:
  Local genus symbol at 2: 1^8

julia> L = mukai_lattice(:Ab; extended = true);

julia> genus(L)
Genus symbol for integer lattices
Signatures: (5, 0, 5)
Local symbol:
  Local genus symbol at 2: 1^10
```

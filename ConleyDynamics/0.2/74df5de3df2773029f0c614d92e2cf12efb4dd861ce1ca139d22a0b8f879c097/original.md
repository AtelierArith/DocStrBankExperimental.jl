```
sc, vfG, vfC = example_torsion_chaos(n::Int, p::Int)
```

Create a triangulation of a space with 1-dimensional torsion, as well as two Forman vectr fields on this complex.

The function returns a simplicial complex `sc` which has the following integer homology groups:

  * In dimension 0 it is the group of integers.
  * In dimension 1 it is the integers modulo `n`.
  * In dimension 2 it is the trivial group.

In other words, the simplicial complex has nontrivial torsion in dimension 1. It is a triangulation of an `n`-gon, in which all boundary edges are oriented counterclockwise, and all of these edges are identified. The parameter `p` specifies the characteristic of the underlying field.

In addition, two Forman vector fields `vfG` and `vfC` are returned. The first one is a gradient vector field whose connection matrix has a large connection matrix entry. In fact, if `p` is any prime larger than `n` then there will be an entry `n` in the matrix. The scond Forman vector field contains a chaotic Morse set. This Morse set will have trivial Morse index for most `p`. On the other hand, for prime `p = n` the set has the Morse index of an unstable  periodic orbit.

# Examples

```jldoctest
julia> sc, vfG, vfC = example_torsion_chaos(3,7);

julia> homology(sc)
3-element Vector{Int64}:
 1
 0
 0

julia> cmG = connection_matrix(sc, vfG);

julia> sparse_show(cmG.matrix)
[0   0   0]
[0   0   3]
[0   0   0]

julia> print(cmG.labels)
["0w", "0w0x", "0w0x1s"]

julia> cmC = connection_matrix(sc, vfC);

julia> sparse_show(cmC.matrix)
[0]

julia> print(cmC.labels)
["0w"]

julia> msC, psC = morse_sets(sc, vfC, poset=true);

julia> [conley_index(sc, mset) for mset in msC]
2-element Vector{Vector{Int64}}:
 [1, 0, 0]
 [0, 0, 0]

julia> psC
2×2 Matrix{Bool}:
 0  1
 0  0

julia> length.(msC)
2-element Vector{Int64}:
  1
 26
```

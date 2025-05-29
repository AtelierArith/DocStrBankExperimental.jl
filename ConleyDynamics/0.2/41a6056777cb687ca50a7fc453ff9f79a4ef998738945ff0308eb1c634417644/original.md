```
sc = simplicial_torsion_space(n::Int, p::Int)
```

Create a triangulation of a space with 1-dimensional torsion.

The function returns a simplicial complex which has the following integer homology groups:

  * In dimension 0 it is the group of integers.
  * In dimension 1 it is the integers modulo `n`.
  * In dimension 2 it is the trivial group.

In other words, the simplicial complex has nontrivial torsion in dimension 1. It is a triangulation of an `n`-gon, in which all boundary edges are oriented counterclockwise, and all of these edges are identified. The parameter `p` specifies the characteristic of the underlying field.

# Examples

```jldoctest
julia> println(homology(simplicial_torsion_space(6,2)))
[1, 1, 1]

julia> println(homology(simplicial_torsion_space(6,3)))
[1, 1, 1]

julia> println(homology(simplicial_torsion_space(6,5)))
[1, 0, 0]
```

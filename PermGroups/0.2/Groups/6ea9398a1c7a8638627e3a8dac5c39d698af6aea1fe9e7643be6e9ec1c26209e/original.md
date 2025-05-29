This module gives some basic functionality on groups.

`Group`  is  an  abstract  type,  but  the  following is assumed of a group `G` of one of its concrete implementations:

  * The function `gens(G)` returns the list of generators of `G`.
  * The function `one(G)` returns the identity element of `G`.

# Examples

```julia-repl
julia> G=Group(Perm(1,2),Perm(1,2,3))
Group((1,2),(1,2,3))

julia> gens(G)
2-element Vector{Perm{Int16}}:
 (1,2)
 (1,2,3)

julia> ngens(G)
2

julia> minimal_words(G)
OrderedDict{Perm{Int16}, Vector{Int64}} with 6 entries:
  ()      => []
  (1,2)   => [1]
  (1,2,3) => [2]
  (1,3)   => [1, 2]
  (2,3)   => [2, 1]
  (1,3,2) => [2, 2]
```

There  is a constructor of a group with arbitrary type elements, `Group(l)` where  `l isa AbstractVector{T}` constructs a `Groupof{T}` which knows only the general methods in this module. The examples above use `Group(AbstractVector{<:Perm})`  which constructs  a `PermGroup`  which has more efficient methods.

for  further information on  the functions defined  in this module, look at the  docstrings of `Group,  gens, ngens, comm,  orbit, orbits, transversal, words_transversal,  centralizer,  stabilizer,  center,  normalizer,  words, minimal_words,   word,  in,   elements,  length,   order,  conjugacy_class, conjugacy_classes, classreps, nconjugacy_classes, fusion_conjugacy_classes, position_class,  isabelian,  iscyclic,  istrivial,  rand, transporting_elt, intersect, Hom, kernel, Coset`

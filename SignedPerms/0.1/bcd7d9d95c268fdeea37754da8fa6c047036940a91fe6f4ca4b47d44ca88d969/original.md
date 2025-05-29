A  signed permutation of `1:n` is  a permutation of the set `-n,…,-1,1,…,n` which  preserves the  pairs `(-i,i)`.  It is  represented internally as the images of `1:n`. It is printed as a product of signed cycles.

# Examples

```julia-repl
julia> SPerm([-2,-1,-3])
SPerm{Int64}: (1,-2)(3,-3)
```

The group of signed permutations of `1:n` is called the hyperoctaedral group.

```
julia> W=hyperoctaedral_group(2)
Group([(1,-1),(1,2)])

julia> elements(W)
8-element Vector{SPerm{Int8}}:
 ()
 (1,-1)
 (1,2)
 (1,-2,-1,2)
 (1,2,-1,-2)
 (1,-2)
 (2,-2)
 (1,-1)(2,-2)
```

A  motivation for my use of signed  permutations is to find if two matrices differ  only by a simultaneous signed permutation of lines and columns. See the example below with `SPerm(m,n;dims=(1,2))`.

The  type  of  signed  permutations  is  `SPerm{T}`  where  `T<:Integer`, a `struct`  with one  field, a  `Vector{T}` which  holds the  image of `1:n`. Using a `T` different than `Int` may possibly save space or time. If `T` is not  specified we  take it  to be  `Int16` since  this is a good compromise between speed and compactness.

`SPerm`s  have methods `copy, hash, ==, isless`  (total order) so they can be keys in hashes or elements of sets; two `SPerm`s are equal if they move the same points to the same images. For instance,

```julia-repl
julia> SPerm([-2,-1,-3])==SPerm([-2,-1,-3,4])
true
```

`SPerm`s are considered as scalars for broadcasting.

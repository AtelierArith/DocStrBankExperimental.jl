This package implements permutations and some functions of them. It depends only  on  the  package  `Combinat`.

This  package  follows  the  design  of  permutations  in the GAP language. `Perm`s  are permutations  of the  set `1:n`,  represented internally  as a vector  of `n`  integers holding  the images  of `1:n`.  The integer `n` is called  the degree  of the  permutation. In  this package,  as in  GAP (and contrary  to the philosophy of Magma or the package `Permutations.jl`), two permutations of different  degrees  can  be  multiplied (the result has the larger  degree). Two permutations  are equal if  and only if  they move the same points in the same way, so two permutations of different degree can be equal; the degree is thus an implementation detail so usually it should not be used. One should rather use the function `last_moved`.

This  design makes it  easy to multiply  permutations coming from different groups, like a group and one of its subgroups. It has a negligible overhead compared to the design where the degree is fixed.

The default constructor for a permutation uses the list of images of `1:n`, like  `Perm([2,3,1,5,4,6])`.  Often  it  is  more  convenient  to use cycle decompositions:    the   above   permutation    has   cycle   decomposition `(1,2,3)(4,5)`    thus   can   be    written   `Perm(1,2,3)*Perm(4,5)`   or `perm"(1,2,3)(4,5)"`  (this last form  can parse a  permutation coming from GAP  or the default printing at the REPL).  The list of images of `1:n` can be  recovered from the permutation by  the function `perm`; note that equal permutations  with different degrees will  have different `perm`. Note that the  default constructor  tests the  validity of  the input  by calling the `julia` function `isperm`. To have a faster constructor which does not test the input, use the keyword argument `check=false`.

The  complete type of a permutation  is `Perm{T}` where `T<:Integer`, where `Vector{T}`  is the type of the vector which holds the image of `1:n`. This can be used to save space or time. For instance `Perm{UInt8}(1,2,3)` can be used for Weyl groups of rank≤8 since they permute at most 240 roots. If `T` is  not specified we take it to be  `Int16` since this is a good compromise between   speed,  compactness  and  possible  size  of  `n`.  One  can  mix permutations of different integer types; they are promoted to the wider one when multiplying.

# Examples of operations with permutations

```julia-repl
julia> a=Perm(1,2,3)
(1,2,3)

julia> perm(a)
3-element Vector{Int16}:
 2
 3
 1

julia> a==Perm(perm(a))
true

julia> b=Perm(1,2,3,4)
(1,2,3,4)

julia> a*b     # product
(1,3,2,4)

julia> inv(a)  # inverse
(1,3,2)

julia> a/b     # quotient  a*inv(b)
(3,4)

julia> a\b     # left quotient inv(a)*b
(1,4)

julia> a^b     # conjugation inv(b)*a*b
(2,3,4)

julia> b^2     # square
(1,3)(2,4)

julia> 1^a     # image by a of point 1
2

julia> one(a)  # trivial permutation
()

julia> sign(a) # signature of permutation
1

julia> order(a) # order (least trivial power) of permutation
3

julia> last_moved(a)
3

julia> first_moved(a)
1

julia> Perm{Int8}(a) # convert a to Perm{Int8}
Perm{Int8}: (1,2,3)

julia> Matrix(b)  # permutation matrix of b
4×4 Matrix{Bool}:
 0  1  0  0
 0  0  1  0
 0  0  0  1
 1  0  0  0
```

```julia-rep1
julia> randPerm(10) # random permutation of 1:10
(1,8,4,2,9,7,5,10,3,6)
```

`Perm`s have methods `copy`, `hash`, `==`, so they can be keys in hashes or elements  of sets; two permutations are equal  if they move the same points to  the same images. They have methods `cmp`, `isless` (lexicographic order on   moved  points)  so  they  can  be  sorted.  `Perm`s  are  scalars  for broadcasting.

Other  methods on  permutations are  `cycles, cycletype, reflection_length, mappingPerm, restricted, support, sortPerm, Perm_rowcol, preimage, randPerm`.

No  method is given in  this package to enumerate  `Perm`s; you can use the method  `permutations` from `Combinat`,  iterate `Combinat.Permutations` or iterate the elements of `symmetric_group` from `PermGroups`.

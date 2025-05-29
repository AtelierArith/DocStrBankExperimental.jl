This  package deals with  finite posets. 

There  are two types of  posets. A "canonical poset"  or `CPoset` is on the elements  `1:n`  where  `n=length(P)`.  A  `Poset`  is  on  a given list of elements  which can be of any type. A `Poset` internally contains a`CPoset` which  works on the indices  of the elements, which  is more efficient than working  with the elements themselves.  For efficiency, many functions work on  the internal `CPoset` by transforming  their input to indices and their output to elements.

A  `CPoset` `p` contains one of the following data:

  * `hasse(p)`:  a list representing  the Hasse diagram  of the poset: the `i`-th  entry is the list of elements which cover (are immediate  successors of) `i`, that  is the list of `j` such that `i<j` and there is no `k` such that `i<k<j`.
  * `incidence(p)`: a  boolean matrix  such that `incidence[i,j]==true` iff `i<=j`. This is sometimes called the ζ-matrix of the poset.

Some  computations work better on the  incidence matrix, and some others on the  Hasse diagram.  If needed  for a  computation and  missing, one of the above  data is computed from the other. This may take some substantial time for large posets.

There  are several ways of defining a  poset. One way is entering the Hasse diagram:

```julia-repl
julia> p=CPoset([[2,3],[4],[4],Int[]])
1<2,3<4
```

As  seen above,  `p` is  displayed as  a list  of covering  maximal chains; elements  which are equivalent for the poset (have the same cover and cover the same elements) are printed together separated by commas.

```julia-repl
julia> length(p) # the number of elements of `p`
4

julia> incidence(p)
4×4 Matrix{Bool}:
 1  1  1  1
 0  1  0  1
 0  0  1  1
 0  0  0  1

julia> linear_extension(p) # a total order compatible with p
4-element Vector{Int64}:
 1
 2
 3
 4
```

A `Poset` is constructed from a `CPoset` and a list of elements

```julia-repl
julia> P=Poset(p,[:a,:b,:c,:d])
a<b,c<d

julia> P.C # the CPoset attached to P
1<2,3<4
```

A  convenient  constructor  for  `Poset`s  takes  a  function  representing `isless`  for the poset and  the list of elements  and constructs the poset from  the incidence matrix, computed by  applying the function to each pair of  elements. For `isless` one can  give either a function implementing `<` or a function implementing `≤` (it is `and`-ed with `!=` in any case).

```julia-repl
julia> l=vec(collect(Iterators.product(1:2,1:2)))
4-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (2, 1)
 (1, 2)
 (2, 2)

julia> P=Poset((x,y)->all(map(<=,x,y)),l)
(1, 1)<(2, 1),(1, 2)<(2, 2)

julia> eltype(P) # the type of the elements of P
Tuple{Int64, Int64}

julia> summary(P) # useful for big posets
"Poset{Tuple{Int64, Int64}} of length 4"
```

A  poset  can  also  be  constructed  from  an incidence matrix so the last example could also be entered as

```julia-repl
julia> P=Poset(CPoset([all(map(<=,x,y)) for x in l, y in l]),l)
(1, 1)<(2, 1),(1, 2)<(2, 2)
```

Flexibility  on  printing  a  `Poset`  is  obtained by setting the function `show_element`  which takes as arguments an  `IO`, the poset, and the index of the element to print:

```julia-repl
julia> P.show_element=(io,p,n)->join(io,p.elements[n],".");

julia> P
1.1<2.1,1.2<2.2

julia> delete!(P,:show_element); # back to default
```

The above fancy printing applies only when printing at the REPL or in pluto or  Jupyter. The default printing  gives a form which  can be input back in Julia

```julia-rep1
julia> print(P) 
Poset(CPoset([[2, 3], [4], [4], Int64[]]),[(1, 1), (2, 1), (1, 2), (2, 2)])
```

A  poset can be specified  by a list of  tuples specifying order relations. The  transitive closure  of these  relations is  computed, resulting  in an incidence  matrix from which the poset  is constructed. The elements of the poset, if not specified separately, are all the elements that appear in the tuples.

```julia-repl
julia> Poset([(:a,:b),(:c,:d)])
a<b
c<d

julia> CPoset([(1,3),(2,5)]) # the CPoset is on 1:maximum(entries)
4
1<3
2<5
```

To get the order relation `≤` or `<` of the poset `p` between elements `i` and `j` just call `≤(p,i,j)` or `<(p,i,j)`. 

```julia-repl
julia> ≤(P,(1,1),(2,1))
true

julia> ≤(P.C,1,2) # the same
true
```

Intervals in a poset can be computed with strict or not bounds.

```julia-repl
julia> interval(P,≤,(1,2)) # elements below (1,2)
2-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (1, 2)

julia> interval(P,≥,(1,2)) # elements above (1,2)
2-element Vector{Tuple{Int64, Int64}}:
 (1, 2)
 (2, 2)

julia> interval(P,<,(1,2)) # elements strictly below (1,2)
1-element Vector{Tuple{Int64, Int64}}:
 (1, 1)

julia> interval(P,≥,(2,1),≤,(2,2)) # elements between (2,1) and (2,2)
2-element Vector{Tuple{Int64, Int64}}:
 (2, 1)
 (2, 2)

julia> interval(P,>,(1,1),<,(2,2)) # elements strictly between
2-element Vector{Tuple{Int64, Int64}}:
 (2, 1)
 (1, 2)
julia> interval(P.C,>,1,<,4) # in terms of indices
2-element Vector{Int64}:
 2
 3
```

A sample of other functions available on posets:

```julia-repl
julia> maximal_chains(P)
2-element Vector{Vector{Tuple{Int64, Int64}}}:
 [(1, 1), (2, 1), (2, 2)]
 [(1, 1), (1, 2), (2, 2)]

julia> height(P) # the length of a maximal chain
3

julia> moebius_matrix(P)
4×4 Matrix{Int64}:
 1  -1  -1   1
 0   1   0  -1
 0   0   1  -1
 0   0   0   1

julia> minima(P)
1-element Vector{Tuple{Int64, Int64}}:
 (1, 1)

julia> maxima(P)
1-element Vector{Tuple{Int64, Int64}}:
 (2, 2)

julia> Q=CPoset(:chain,3)
1<2<3

julia> P1=Poset(Q) # transformed to a Poset with elements 1:3
1<2<3

julia> P⊕ P1 # the ordinal sum
(1, 1)<(2, 1),(1, 2)<(2, 2)<1<2<3

julia> P1*P1
(1, 1)<(2, 1)<(3, 1)<(3, 2)<(3, 3)
(1, 1)<(1, 2)<(2, 2)<(3, 2)
(2, 1)<(2, 2)
(1, 2)<(1, 3)<(2, 3)<(3, 3)
(2, 2)<(2, 3)

julia> P1⊗ P1 # the ordinal product
(1, 1)<(1, 2)<(1, 3)<(2, 1)<(2, 2)<(2, 3)<(3, 1)<(3, 2)<(3, 3)
```

Finally `showpic(p)` where `p` is a `CPoset` or a `Poset` gives a graphical display  of the  poset provided  you have  the command  `dot` of `graphviz` installed. It then uses the xdg "open" command to open the resulting `.png` file. This works on Linux and MacOs but I could not try it on Windows.

see the on-line help on `⊕, ⊗,  +, *, chains, chainpoly, covering_chains, coxeter_matrix,  dual,  hasse,  height, incidence,  induced,  interval,  is_join_semilattice,  is_meet_semilattice,  linear_extension,  linear_extensions,  nlinear_extensions,  rand_linear_extension,  is_linear_extension,  maxima, maximal_chains,  antichains, minima, moebius,  moebius_matrix,  partition,  showpic, transitive_closure` for more information

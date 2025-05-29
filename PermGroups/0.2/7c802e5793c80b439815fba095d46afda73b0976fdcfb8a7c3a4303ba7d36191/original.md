This  module is a port  of some GAP functionality  on permutation groups. A `PermGroup` is a `Group` where `gens` are `Perm`s. It depends on the modules `Groups` and `Perms` which could be independent packages on their own.

```julia-repl
julia> G=Group([Perm(i,i+1) for i in 1:2])
Group((1,2),(2,3))

julia> collect(G) # PermGroups are iterators over their elements
6-element Vector{Perm{Int16}}:
 ()
 (1,2)
 (1,3,2)
 (2,3)
 (1,2,3)
 (1,3)

julia> last_moved(G)  # maximum moved point of any element of `G`
3

julia> orbits(G) # the orbits are orbits on points it moves
1-element Vector{Vector{Int16}}:
 [1, 2, 3]

julia> Perm(1,2) in G
true

julia> Perm(1,2,4) in G
false
```

`elements`,   `in`  and   other  functions   are  computed   on  `G`  using Schreier-Sims theory, that is computing the following

```julia-repl
julia> get_stabchain(G)
b:1 c:Group((1,2),(2,3))
  δ:1=>(),2=>(1,2),3=>(1,3,2)
b:2 c:Group((2,3))
  δ:2=>(),3=>(2,3)
```

See the docstring of `stabchain` for explanations.

There are efficient methods for `PermGroups` for the functions `in, length, elements,   position_class`.  The  function   `on_classes`  determines  the permutation  of the conjugacy classes effected by an automorphism. Finally, we   give  application  to  the  group   of  simultaneous  row  and  column permutations of a matrix: see `stab_onmats, Perm`.

finally, benchmarks on julia 1.9

```benchmark
julia> @btime collect(symmetric_group(8));
  1.921 ms (50128 allocations: 3.29 MiB)

julia> @btime words(symmetric_group(8));
  6.441 ms (80971 allocations: 10.88 MiB)

julia> @btime elements(symmetric_group(8)); # Gap takes 8 ms
  1.565 ms (49539 allocations: 3.71 MiB)

julia> rubik_gens=[
  perm"(1,3,8,6)(2,5,7,4)(9,33,25,17)(10,34,26,18)(11,35,27,19)",
  perm"(9,11,16,14)(10,13,15,12)(1,17,41,40)(4,20,44,37)(6,22,46,35)",
  perm"(17,19,24,22)(18,21,23,20)(6,25,43,16)(7,28,42,13)(8,30,41,11)",
  perm"(25,27,32,30)(26,29,31,28)(3,38,43,19)(5,36,45,21)(8,33,48,24)",
  perm"(33,35,40,38)(34,37,39,36)(3,9,46,32)(2,12,47,29)(1,14,48,27)",
  perm"(41,43,48,46)(42,45,47,44)(14,22,30,38)(15,23,31,39)(16,24,32,40)"];

julia> @btime length(Int128,Group(rubik_gens)) # Gap takes 5ms
  4.906 ms (104874 allocations: 13.64 MiB)
43252003274489856000
```

Note  the use of  `Int128` in `length`:  the computation does  not fit in an `Int64`.

`Category{TO,TM}` is the type of a finite category whose objects are of type `TO` and maps of type `TM`.  It is represented as a `struct` with two fields:

  * `obj::Vector{TO}` the objects
  * `atoms::Vector{Vector{Pair{TM,Int}}}` a vector representing the atoms (generators) of the category. It is such that `atoms[i]` is a `Vector` of  pairs `m=>j` representing a map `m` from `obj[i]` to `obj[j]`. If the julia objects of type `TM` belong to a monoid, a general map can be represented as a triple `(i,m,j)` where `m` is of type `TM` representing a map from `obj[i]` to `obj[j]`.

A category is graphically shown by giving the `:graph` io property:

```julia-rep1
julia> W=coxsym(4);M=BraidMonoid(W)
BraidMonoid(𝔖 ₄)

julia> xprint(conjcat(M(1,1,2,2,3));graph=true)
category with 4 objects and 8 generating maps
      1232       12       213       213       213       32 
213.32―――➔ 12.213―➔ 213.12――➔ 12.213――➔ 213.32――➔ 32.213―➔ 213.32
      1321       213 
213.12―――➔ 32.213――➔ 213.12
```

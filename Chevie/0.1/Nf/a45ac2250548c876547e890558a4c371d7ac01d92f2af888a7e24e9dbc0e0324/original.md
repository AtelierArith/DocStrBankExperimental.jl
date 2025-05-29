`Aut(F::NumberField,k::Union{Integer,Mod})`

The  *Galois  automorphism*  `σₖ`  of  the  cyclotomic field `CF(n)` raises `n`-th  roots of unity to the power `k`; it exists for `k` prime to `n`. If `F`  is a subfield of `CF(n)`, the elements of the orbit of `σₖ` modulo the stabilizer of `F` in the Galois group `galois(CF(n))` have same restriction to `F`. An automorphism of `F` is represented by a canonical representative `σₗ` of this orbit. This is the result of `Aut(F,k)`. The number `k` can be given as an integer or as `Mod(k,n)`.

```julia-repl
julia> F=NF(root(5))
NF(5,-1₅)

julia> s=Aut(F,3)
Aut(NF(5,-1₅),2₅)

julia> root(5)^s # action of s on a Cyc
Cyc{Int64}: -√5
```

Number  fields are the finite extensions of  `ℚ`. The only ones that we can handle  at the  moment are  subfields of  cyclotomic fields,  that is whose elements  are `Cyc`s; they are also  characterized as the number fields `K` such  that `Gal(K/ℚ)` is abelian.  For example, `ℚ (√5)`  is a number field that is not cyclotomic but contained in the cyclotomic field `ℚ (ζ₅)`.

The default constructor for a number field takes some numbers as arguments and constructs the smallest number field containing its arguments.

```julia-repl
julia> F=NF(E(5)) # the full cyclotomic field prints as CF
CF(5)

julia> K=NF(root(5)) # a subfield
NF(5,-1₅)

julia> conductor(K) # smallest n such that K is a subfield of CF(n)
5

julia> E(5)+E(5,-1) in NF(root(5)) # test if an element is in the subfield
true
```

A  number  field  `K`  is  printed  by  given the conductor of the smallest cyclotomic field `F` containing it, and generators of the stabilizer of `K` in  the galois group  of `F`. Above  `NF(5,-1₅)` represents the subfield of `CF(5)` stable by complex conjugacy.

```julia-repl
julia> elements(galois(F))
4-element Vector{Chevie.Nf.NFAut}:
 Aut(CF(5),1₅)
 Aut(CF(5),2₅)
 Aut(CF(5),-1₅)
 Aut(CF(5),-2₅)
```

The  element of the galois  group of `CF(5)` printed  `-2₅` acts by raising the  fifth roots of  unity to the  power -2. Thus  `-1₅` represents complex conjugacy.

```julia-repl
julia> NF(root(3),root(5)) # here the stabilizer needs 2 generators
NF(60,-11₆₀,-1₆₀)
```

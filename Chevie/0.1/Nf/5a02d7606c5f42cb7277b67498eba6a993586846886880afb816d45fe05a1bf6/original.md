`galois(F::NumberField)` Galois group of `F` over `ℚ`

the  Galois group of `F`, a number  field of conductor `n`, is the quotient of  the Galois  group of  `CF(n)`, isomorphic  to the  multiplicative group `(ℤ/n)ˣ`,  by  the  stabilizer  of  `F`.  It  is given as a group of Galois automorphisms (see `Aut`).

```julia-repl
julia> K=CF(5)
CF(5)

julia> F=NF(root(5))
NF(5,-1₅)

julia> galois(K)
Group(Chevie.Nf.NFAut[Aut(CF(5),2₅)])

julia> elements(galois(K))
4-element Vector{Chevie.Nf.NFAut}:
 Aut(CF(5),1₅)
 Aut(CF(5),2₅)
 Aut(CF(5),-1₅)
 Aut(CF(5),-2₅)

julia> elements(galois(F))
2-element Vector{Chevie.Nf.NFAut}:
 Aut(NF(5,-1₅),1₅)
 Aut(NF(5,-1₅),2₅)
```

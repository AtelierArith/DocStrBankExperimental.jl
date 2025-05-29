`galois(F::NumberField)` Galois群 `F` の ℚ に対する

導体 `n` の数体 `F` の Galois群は、Galois群 `CF(n)` の商であり、これは乗法群 `(ℤ/n)ˣ` に同型で、`F` の安定化群によって割られます。これは Galois自己同型の群として与えられます（`Aut` を参照）。

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

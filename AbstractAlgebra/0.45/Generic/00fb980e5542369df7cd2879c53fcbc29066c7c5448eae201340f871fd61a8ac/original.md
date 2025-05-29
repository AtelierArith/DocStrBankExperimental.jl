```
normal_form(f::FreeAssociativeAlgebraElem{T}, g::Vector{FreeAssociativeAlgebraElem{T}}, aut::AhoCorasickAutomaton)
```

Assuming `g` is a Groebner basis and `aut` an Aho-Corasick automaton for the elements of `g`, compute the normal form of `f` with respect to `g`

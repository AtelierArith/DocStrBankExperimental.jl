```
normal_form(f::FreeAssociativeAlgebraElem{T}, g::Vector{FreeAssociativeAlgebraElem{T}}, aut::AhoCorasickAutomaton)
```

`g` がグレブナー基底であり、`aut` が `g` の要素に対するアホ・コラスックオートマトンであると仮定すると、`g` に関して `f` の正規形を計算します。

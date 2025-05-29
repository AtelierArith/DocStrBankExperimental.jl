```
coprime_base_push!(S::Vector{RingElem}, a::RingElem) -> Vector{RingElem}
```

与えられた互いに素な要素の配列 $S$ に新しい要素を挿入します。すなわち、`push(S, a)` のための互いに素な基底を見つけます。

```
evaluate(::BinaryHammingDistance, a, b)
evaluate(::BinaryHammingDistance, a::AbstractVector, b::AbstractVector) where {T<:Unsigned}
```

ビット型およびビット型の配列に対するバイナリハミング距離を計算します。

```
 divexact(a::LocalizedEuclideanRingElem{T}, b::LocalizedEuclideanRingElem{T}, checked::Bool = true)  where {T <: RingElem}
```

与えられた局所化の要素 'c' を返します。すなわち、`c`*$b$ = $a$ となる要素が存在する場合です。'checked = true' の場合、結果は与えられた局所化の要素であることを確認するためにチェックされます。

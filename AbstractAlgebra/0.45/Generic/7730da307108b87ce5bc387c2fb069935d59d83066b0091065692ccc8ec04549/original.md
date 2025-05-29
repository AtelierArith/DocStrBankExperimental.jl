```
 divexact(a::LocalizedEuclideanRingElem{T}, b::LocalizedEuclideanRingElem{T}, checked::Bool = true)  where {T <: RingElem}
```

Returns element 'c' of given localization s.th. `c`*$b$ = $a$ if such element exists. If 'checked = true' the result is checked to ensure it is an element of the given localization.

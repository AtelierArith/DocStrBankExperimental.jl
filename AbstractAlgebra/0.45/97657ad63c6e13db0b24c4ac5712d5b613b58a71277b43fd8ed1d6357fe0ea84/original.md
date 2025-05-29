```
+(x::MatrixElem{T}, y::T) where {T <: RingElem}
```

Return $x + S(y)$ where $S$ is the parent of $x$.

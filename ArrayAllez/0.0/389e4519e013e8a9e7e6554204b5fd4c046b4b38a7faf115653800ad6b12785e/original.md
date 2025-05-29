```
log!(A)
log_(A) ≈ log!(similar(A), A)
log0(A) = log.(A)
```

Element-wise in-place natural logarithm, and friends. Multi-threaded when `length(A) >= 5000`. Will be handled by `Yeppp` or `AppleAccelerate` or `IntelVectorMath` if you load one of them.

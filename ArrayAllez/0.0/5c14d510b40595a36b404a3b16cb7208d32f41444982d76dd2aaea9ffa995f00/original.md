```
exp!(A)
exp_(A) = exp!(similar(A), A)
exp0(A) ≈ exp.(A)
```

Element-wise in-place exponential, and friends. Multi-threaded when `length(A) >= 5000`. Will be handled by `Yeppp` or `AppleAccelerate` or `IntelVectorMath` if you load one of them, note that `Yeppp` may well be slower.

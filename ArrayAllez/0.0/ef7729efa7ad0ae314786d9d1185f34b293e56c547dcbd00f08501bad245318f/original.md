```
inv!(A) ≈ 1 ./ A
inv!(A, b::Number) ≈ b ./ A
```

And `inv_(A)` which copies, and `inv0(A)` simple broadcasting. Multi-threaded when `length(A) >= 100000`. Will be handled by `AppleAccelerate` if you load it.

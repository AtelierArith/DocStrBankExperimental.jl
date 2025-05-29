```
dropout!(B, A, p; [dims])
```

This does exactly `B .= dropout(A, p; dims)`, or rather, it's the implementation of out-of-place [`dropout`](@ref).

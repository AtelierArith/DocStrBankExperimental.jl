```
boxdot!(Y, A, B, α=1, β=0)
```

In-place version of `boxdot`, i.e. `Y .= (A ⊡ B) .* β .+ Y .* α`. Like 5-argument `mul!`, the use of `α, β` here requires Julia 1.3 or later.

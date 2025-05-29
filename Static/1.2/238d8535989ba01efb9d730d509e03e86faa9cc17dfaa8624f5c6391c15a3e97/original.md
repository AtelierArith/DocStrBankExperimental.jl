```
StaticInt(N::Int) -> StaticInt{N}()
```

A statically sized `Int`. Use `StaticInt(N)` instead of `Val(N)` when you want it to behave like a number.

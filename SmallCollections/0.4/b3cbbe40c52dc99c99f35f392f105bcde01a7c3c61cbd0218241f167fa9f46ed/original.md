```
pop(s::S) where S <: SmallBitSet -> Tuple{S, Int}
```

Return the pair `(t, x)` where `x` is the smallest element from `s` and `t` is the set `s` with `x` deleted. The set `s` must be non-empty.

See also `Base.pop!`, `BangBang.pop!!`.

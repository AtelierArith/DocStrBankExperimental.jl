```
pop(s::S, x, default::T) where S <: SmallBitSet -> Tuple{S, Union{Int,T}}
```

If `s` contains `x`, return the pair `(t, x)` where `t` is the set `s` with `x` deleted. Otherwise return `(s, default)`

See also `Base.pop!`, `BangBang.pop!!`.

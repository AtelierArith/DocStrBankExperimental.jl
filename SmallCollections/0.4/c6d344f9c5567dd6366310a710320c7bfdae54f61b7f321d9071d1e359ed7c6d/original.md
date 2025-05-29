```
delete(s::S, x) where S <: SmallBitSet -> S
```

If `s` contains `x`, return the set obtained by deleting that element. Otherwise return `s`.

See also `Base.delete!`, `BangBang.delete!!`.

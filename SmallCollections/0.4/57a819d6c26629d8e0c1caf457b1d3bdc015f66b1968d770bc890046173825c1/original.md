```
push(s::S, xs...) where S <: SmallBitSet -> S
```

Return the `SmallBitSet` obtained from `s` by adding the other arguments `xs`.

See also `Base.push!`, `BangBang.push!!`.

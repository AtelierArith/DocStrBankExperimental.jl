```
push(v::V, xs...) where V <: AbstractCapacityVector -> V
```

Return the `AbstractCapacityVector` obtained from `v` by appending the arguments `xs`.

See also `Base.push!`, `BangBang.push!!`.

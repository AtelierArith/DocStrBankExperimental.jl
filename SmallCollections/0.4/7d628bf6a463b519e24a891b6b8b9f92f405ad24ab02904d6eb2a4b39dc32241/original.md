```
pushfirst((v::V, xs...) where V <: AbstractCapacityVector -> V
```

Return the `AbstractCapacityVector` obtained from `v` by prepending the arguments `xs`.

See also `Base.pushfirst!`, `BangBang.pushfirst!!`.

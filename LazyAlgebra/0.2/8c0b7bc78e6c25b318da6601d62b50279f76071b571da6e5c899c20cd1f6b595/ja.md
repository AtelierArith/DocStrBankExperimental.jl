```
RankOneOperator(u, v) -> A
```

は、2つの*ベクトル* `u` と `v` によって定義されるランク1の線形演算子 `A = u⋅v'` を生成し、次のように振る舞います：

```
A*x  -> vscale(vdot(v, x)), u)
A'*x -> vscale(vdot(u, x)), v)
```

参照： [`SymmetricRankOneOperator`](@ref), [`LinearMapping`](@ref),           [`apply!`](@ref), [`vcreate`](@ref).

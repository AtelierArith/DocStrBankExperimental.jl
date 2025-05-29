```
SymmetricRankOneOperator(u) -> A
```

は、*ベクトル* `u` によって定義される対称ランク1演算子 `A = u⋅u'` を生成し、次のように振る舞います：

```
A'*x -> A*x
A*x  -> vscale(vdot(u, x)), u)
```

参照： [`RankOneOperator`](@ref), [`LinearMapping`](@ref),           [`Trait`](@ref) [`apply!`](@ref), [`vcreate`](@ref).

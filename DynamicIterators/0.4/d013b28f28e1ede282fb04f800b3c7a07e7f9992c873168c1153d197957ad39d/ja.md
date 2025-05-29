```
evolve(f)
```

進化に対応するDynamicIteratorを作成します

```
    x = f(x)
```

整数キーはデフォルトでインクリメントします。 整数制御はデフォルトでキー（および繰り返し）です。

```
julia> collect(take(from(Evolve(x->x + 1), 10), 5))
5-element Array{Any,1}:
 10
 11
 12
 13
 14
```

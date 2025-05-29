```
multiplicities(::Bool)
```

明示的に重複度を表示したい場合は、スイッチ `multiplicities` をオンにすることができます。例えば

```Julia
julia> Algebra.on(:multiplicities); Algebra.solve(:(x^2==2x-1),:x)
```

は次の結果を返します

```Julia
(:(x = 1), :(x = 1))
```

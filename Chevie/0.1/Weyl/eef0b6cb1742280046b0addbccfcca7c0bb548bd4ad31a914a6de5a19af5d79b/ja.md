`badprimes(W)`

`W` を Weyl 群とします。素数は `W` に対して *bad* である場合、単純根のいくつかの根の係数を割り切ります。関数 `badprimes` は `W` に対して悪い素数のリストを返します。

```julia-repl
julia> W=coxgroup(:E,8)
E₈

julia> badprimes(W)
3-element Vector{Int64}:
 2
 3
 5
```

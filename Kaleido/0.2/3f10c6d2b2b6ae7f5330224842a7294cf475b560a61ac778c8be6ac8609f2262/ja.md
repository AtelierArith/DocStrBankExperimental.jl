```
nullsetter :: Setter
```

何もしないセッター; すなわち、任意の `x` と `y` に対して `set(x, nullsetter, y) === x` です。

# 例

```jldoctest
julia> using Setfield, Kaleido

julia> set(1, nullsetter, 2)
1
```

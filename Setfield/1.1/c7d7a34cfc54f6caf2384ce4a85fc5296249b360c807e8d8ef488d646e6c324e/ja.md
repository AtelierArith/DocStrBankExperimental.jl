```
@set! assignment
```

`obj = @set obj...` のショートカットです。

# 例

```jldoctest
julia> using Setfield

julia> t = (a=1,)
(a = 1,)

julia> @set! t.a=2
(a = 2,)

julia> t
(a = 2,)
```

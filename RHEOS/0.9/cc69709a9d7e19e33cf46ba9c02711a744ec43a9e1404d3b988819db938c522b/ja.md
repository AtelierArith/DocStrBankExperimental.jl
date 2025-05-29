```
function namedtuple(d::Dict)
function namedtuple(;kwargs...)
```

`namedtuple`は、キーワード引数またはパラメータとして渡された辞書を使用して形成された名前付きタプルを返します。

# 例

```@example
julia> nt = namedtuple(x=1,y=2)
(x = 1, y = 2)
```

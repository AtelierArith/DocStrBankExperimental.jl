```
function dict(nt::NamedTuple)
function dict(;kwargs...)
```

`dict`は、キーワード引数またはパラメータとして渡された名前付きタプルを使用して形成された辞書を返します。

# 例

```@example
julia> d = dict(x=1,y=2)
Dict{Symbol, Int64} with 2 entries:
  :y => 2
  :x => 1
```

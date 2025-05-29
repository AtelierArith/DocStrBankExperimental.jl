```
Tracer{T}(::Type{T}, f, b=1)
```

`f(model, i)`を`b`回ごとに保存します。

`Tracer`が収集したデータを抽出するには、`collect(tracer)`を使用します。この操作はコピーを行うことに注意してください。

```jldoctest
julia> t = Tracer(Int, (model, i) -> @show(i))
Tracer(1, #5, 0-element Array{Int64,1})

julia> learn!(nothing, strategy(MaxIter(3), t))
i = 1
i = 2
i = 3

julia> collect(t)
3-element Array{Int64,1}:
 1
 2
 3
```

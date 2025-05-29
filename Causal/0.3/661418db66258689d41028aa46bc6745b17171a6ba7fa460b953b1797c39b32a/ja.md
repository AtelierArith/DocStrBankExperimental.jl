```julia
applycallbacks(obj)

```

`obj`のコールバックを呼び出します。コールバックがnothingでない場合に限ります。

# 例

```julia
julia> mutable struct MyType{CB}
       x::Int
       callbacks::CB
       end

julia> obj = MyType(5, Callback(condition=obj -> obj.x > 0, action=obj -> println("xは正の数です")));

julia> applycallbacks(obj)
xは正の数です

julia> obj.x = -1
-1

julia> applycallbacks(obj)
```

```
splitarg(arg)
```

関数の引数（定義または関数呼び出しからの）をマッチさせ、`x::Int=2`のような形式を持つ引数を返します。返されるのは`(arg_name, arg_type, is_splat, default)`です。`arg_name`と`default`は存在しない場合は`nothing`になります。例えば：

```julia
julia> map(splitarg, (:(f(a=2, x::Int=nothing, y, args...))).args[2:end])
4-element Array{Tuple{Symbol,Symbol,Bool,Any},1}:
 (:a, :Any, false, 2)
 (:x, :Int, false, :nothing)
 (:y, :Any, false, nothing)
 (:args, :Any, true, nothing)
```

関連情報: [`combinearg`](@ref)

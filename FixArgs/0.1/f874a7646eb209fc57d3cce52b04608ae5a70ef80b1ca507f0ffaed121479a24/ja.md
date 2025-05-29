このパッケージによって生成される型は扱いにくいです。このマクロは便利な構文を許可します。例えば、`@xquoteT func(::Arg1Type, ::Arg2Type)`は型を表現します。

```jldoctest
let func = identity, arg = 1
    typeof(@xquote func(arg)) == @xquoteT func(::typeof(arg))
end

# 出力

true
```

引数が「静的」である場合、それは型の一部であり、値は以下のように注釈されます：

```julia
julia> @xquoteT string(123::::S)
FixArgs.Call{Some{typeof(string)},FrankenTuples.FrankenTuple{Tuple{Val{123}},(),Tuple{}}}
```

```
@named y = foo(x)
@named y[1:10] = foo(x)
@named begin
    y[1:10] = foo(x)
    z = foo(x)
end # returns `[y; z]`
@named y 1:10 i -> foo(x*i)  # これは推奨されません
```

LHS名をモデルに渡します。抽象システムでないものを呼び出すときは、すべてのキーワード引数を`default_to_parentscope`でラップして、シンボリックデフォルトをコンポーネントに渡すときに名前空間が直感的に機能するようにします。

例:

```julia-repl
julia> using ModelingToolkit

julia> foo(i; name) = (; i, name)
foo (generic function with 1 method)

julia> x = 41
41

julia> @named y = foo(x)
(i = 41, name = :y)

julia> @named y[1:3] = foo(x)
3-element Vector{NamedTuple{(:i, :name), Tuple{Int64, Symbol}}}:
 (i = 41, name = :y_1)
 (i = 41, name = :y_2)
 (i = 41, name = :y_3)
```

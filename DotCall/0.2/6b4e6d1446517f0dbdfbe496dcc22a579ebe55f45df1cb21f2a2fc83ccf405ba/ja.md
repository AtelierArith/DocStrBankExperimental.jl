```
add_dotcalls(::Type{DottedT}, dotcalllist)
```

`DottedT`のプロパティを`dotcalllist`に追加し、すでにDotCall化されているプロパティのリストに追加します。

`DottedT`に対してすでにDotCall化されていないプロパティのみが追加されます。以前に追加されたプロパティは更新されません。

`add_dotcalls`は関数であるため、`@dotcallify`とは異なり、`dotcalllist`はリテラルコンテナ（例えば`Tuple`や`Vector`）またはコンテナにバインドされた変数名であることができます。

追加されたプロパティの2タプル（`Tuple`）の`Vector`を返します。つまり、リストにすでに存在しないプロパティです。

# 例

```julia-repl
julia> dotcallified_properties(MyA)
(sx = MyAs.sx, x = MyAs.x, sin = sin, y = 3, mycos = MyAs.var"#1#3"())

julia> add_dotcalls(MyA, (:x, :sx, :cf))
1-element Vector{Tuple{Symbol, Symbol}}:
 (:cf, :cf)

julia> add_dotcalls(MyA, (:x, :sx, :cf))
()
```

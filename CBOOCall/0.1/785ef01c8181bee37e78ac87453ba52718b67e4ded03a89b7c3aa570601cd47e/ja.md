```
add_cboo_calls(::Type{CBOOedT}, cboolist)
```

`cboolist`のプロパティを、すでにcboo-ifiedされた型`CBOOedT`のcboo-call可能なプロパティのリストに追加します。

`CBooedT`に対してすでにCBOO-ifiedされていないプロパティのみが追加されます。以前に追加されたプロパティは更新されません。

`add_cboo_calls`は関数であるため、`@cbooify`とは異なり、`cboolist`はリテラルコンテナ（例えば`Tuple`や`Vector`）またはコンテナにバインドされた変数名であることができます。

追加されたプロパティの2タプル（`Tuple`）の`Vector`を返します。つまり、リストにすでに存在しないプロパティです。

# 例

```julia-repl
julia> cbooified_properties(MyA)
(sx = MyAs.sx, x = MyAs.x, sin = sin, y = 3, mycos = MyAs.var"#1#3"())

julia> add_cboo_calls(MyA, (:x, :sx, :cf))
1-element Vector{Tuple{Symbol, Symbol}}:
 (:cf, :cf)

julia> add_cboo_calls(MyA, (:x, :sx, :cf))
()
```

```
@js_str(s)
```

文字列リテラルを使用して `JSString` を作成し、Juliaからの補間を行います。

# 例

```julia-repl
julia> mystr = "foo"; mydict = Dict("foo" => "bar", "spam" => "eggs");
julia> println(js"const myStr = $mystr; const myObject = $mydict;")
const myStr = "foo"; const myObject = {"spam":"eggs","foo":"bar"};
```

```
@js win expr
```

`expr`をjuliaコードとして解析し、javascriptに直接変換して`win`内で実行し、結果を返します。

`expr`はjuliaコードとして解析され、その後、同等のjavascriptに直接変換されます。juliaに存在しない言語キーワードは、マクロの等価物`@var`、`@new`などで表現できます。

参照: 非同期バージョンの`@js_`。

# 例

```julia-repl
julia> @js win x = 5
5
julia> @js_ win for i in 1:x console.log(i) end
```

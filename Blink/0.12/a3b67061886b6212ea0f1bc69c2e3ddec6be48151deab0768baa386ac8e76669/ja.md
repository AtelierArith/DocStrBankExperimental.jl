```
@js_ win expr
```

`expr`をJavaScriptに変換して非同期的に`win`内で実行し、すぐに戻ります。

`expr`はJuliaコードとして解析され、その後直接同等のJavaScriptに変換されます。Juliaに存在しない言語キーワードは、`@var`、`@new`などのマクロの同等物で表現できます。

参照: 結果を返す同期バージョンの`@js`。

# 例

```julia-repl
julia> @js win x = 5
5
julia> @js_ win for i in 1:x console.log(i) end
```

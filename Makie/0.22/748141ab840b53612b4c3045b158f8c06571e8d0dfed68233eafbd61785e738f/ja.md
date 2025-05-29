```
with_theme(f, theme = Theme(); kwargs...)
```

`theme`を一時的に有効にして`f`を呼び出します。`theme`内の属性は`kwargs`で上書きまたは拡張できます。`f`が成功しても失敗しても、以前のテーマは常にその後に復元されます。

例:

```julia
my_theme = Theme(size = (500, 500), color = :red)
with_theme(my_theme, color = :blue, linestyle = :dashed) do
    scatter(randn(100, 2))
end
```

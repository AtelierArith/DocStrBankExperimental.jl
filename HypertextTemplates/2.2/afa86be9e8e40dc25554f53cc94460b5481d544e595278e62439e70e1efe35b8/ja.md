```
StreamingRender(func)
```

`func`というレンダリング関数を実行するイテラブルで、単一の`io`引数を受け取り、`@render`マクロ呼び出しに渡す必要があります。

```julia
for bytes in StreamingRender(io -> @render io @component {args...})
    write(http_stream, bytes)
end
```

または、`->`構文の代わりに`do`ブロックを使用します。

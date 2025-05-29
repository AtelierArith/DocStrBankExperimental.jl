```
set_timeout(f::Function, w::Webview, interval::Real; [repeat::Bool=false])
```

指定された間隔の後にwebviewのイベントループで呼び出される関数を設定します。`repeat`が`true`の場合、`f`は繰り返し呼び出されます。関数`f`は引数なしで呼び出せる必要があります。

この関数は`clear_timeout(webview, timer_id)`で使用できる`timer_id::Ptr{Cvoid}`を返します。

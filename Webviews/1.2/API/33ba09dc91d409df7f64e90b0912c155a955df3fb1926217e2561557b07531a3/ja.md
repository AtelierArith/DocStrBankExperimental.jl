```
bind_raw(f::Function, w::Webview, name::AbstractString)
```

コールバックをバインドして、指定された名前でグローバル非同期JavaScript関数としてウェブビューに表示されるようにします。コールバックはseqとreqの値を受け取ります。seqパラメータは、`Webviews.return_raw`を使用して値を返すための識別子であり、reqパラメータはJavaScript関数呼び出しから渡された引数を表すJSON配列の文字列です。

コールバック関数は、`f(seq::String, req::String)`メソッドを持っている必要があります。

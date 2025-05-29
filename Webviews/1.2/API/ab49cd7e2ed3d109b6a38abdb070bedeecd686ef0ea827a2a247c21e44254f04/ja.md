```
init(w::Webview, js::AbstractString)
```

新しいページの初期化時にJavaScriptコードを注入します。ウェブビューが新しいページを開くたびに、この初期化コードが実行されます。コードは `window.onload` の前に実行されることが保証されています。

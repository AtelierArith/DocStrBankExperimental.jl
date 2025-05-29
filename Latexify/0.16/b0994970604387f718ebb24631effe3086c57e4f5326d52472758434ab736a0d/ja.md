```
render(::LaTeXString[, ::MIME"mime"]; debug=false, name=tempname(), command="\Large", callshow=true, open=true)
```

与えられた入力を使用してスタンドアロンのドキュメントを表示します。サポートされているMIMEタイプの文字列は「application/pdf」（デフォルト）、「application/x-dvi」、「image/png」、および「image/svg」です。

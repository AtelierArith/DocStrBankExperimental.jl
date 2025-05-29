XMLツリーを走査し、`builder`を使用してエディションのテキストコンテンツを構成します。`n`は解析されたパッセージです。`accum`は、すでに見たテキストの蓄積です。

```julia
edited_text(builder, n)
edited_text(builder, n, accum)

```

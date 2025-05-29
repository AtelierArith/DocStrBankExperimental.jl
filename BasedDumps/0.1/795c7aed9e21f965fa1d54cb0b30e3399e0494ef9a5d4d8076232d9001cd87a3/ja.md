```
textdump(io::IO, txt::AbstractString, base::Integer; offset = 0, len = -1)
```

文字列 `txt` を `baseddump` でダンプします。Julia の文字列は utf-8 テキストとして解釈され、マルチバイト文字はリトルエンディアン順で表示されます。

```
textdump(txt, base; offset = 0, len = -1)
```

このメソッドは前者と同じですが、stdout のみにダンプします。

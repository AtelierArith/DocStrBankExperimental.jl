```
sr"..."
```

この文字列リテラルは、文字列内のすべての特殊文字をエスケープするために使用され、クエリ内で正規表現を使用するのに便利です。

このリテラルは非推奨であり、ユーザーは代わりに `Base.@raw_str` に切り替えるべきです。

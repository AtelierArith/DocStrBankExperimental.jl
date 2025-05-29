```
mapwindows(f, W::AbstractWindows)
```

関数 `f` を `W::Windows2` で表されるすべてのウィンドウに適用します。`f` は `(y,t)->ŷ` の形式でなければならず、`y` と `ŷ` は同じ長さである必要があります。

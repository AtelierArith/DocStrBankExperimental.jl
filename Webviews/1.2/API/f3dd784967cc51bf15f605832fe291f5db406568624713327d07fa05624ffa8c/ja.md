```
navigate!(w::Webview, url::AbstractString)
```

指定されたURLにwebviewをナビゲートします。URLはデータURIである可能性があります。すなわち、`"data:text/html,<html>...</html>"`の形式です。

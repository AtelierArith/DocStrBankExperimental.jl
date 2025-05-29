```
pagefind(; extended::Bool=false)
```

`pagefind` バイナリのための `Cmd` オブジェクトを返します。`extended` が `true` の場合、`pagefind_extended` バイナリが返されます。バイナリの拡張版は遅延アーティファクトであり、`Cmd` が初めて実行されるときにのみダウンロードされることに注意してください。

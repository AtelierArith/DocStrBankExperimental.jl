```
sindex(wrangler::FunctionWrangler, idx, args...)
```

`idx` 番目の関数を args で呼び出します。

この呼び出しは、1 から `idx` までの wrangler を反復処理することに注意してください。オーバーヘッドを最小限に抑えるために、頻繁に呼び出される関数を最初に配置することをお勧めします。

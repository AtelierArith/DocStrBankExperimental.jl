```
XPRS_CALLBACKFROMMASTERTHREAD
```

分枝限定法: MIP コールバックがマスタースレッドでのみ呼び出されるべきかどうかを指定します。(整数)

デフォルト値: `0`

値: 0 : 並列 MIP 中にワーカースレッドでコールバックを呼び出す; 1 : `XPRSmipoptimize` を呼び出したスレッドでのみコールバックを呼び出す。

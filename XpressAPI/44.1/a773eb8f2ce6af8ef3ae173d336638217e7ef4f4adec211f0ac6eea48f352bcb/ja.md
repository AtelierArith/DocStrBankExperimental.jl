```
XPRScreateprob(f, path)
```

`XPRSprob` インスタンスを作成します。

`path` : これが `nothing` でない場合、関数はそのパスで Xpress を初期化します（`XPRSinit` を参照）し、その後 `XPRSprob` インスタンスを作成します。`XPRSprob` インスタンスが破棄されると、Xpress は解放されます。

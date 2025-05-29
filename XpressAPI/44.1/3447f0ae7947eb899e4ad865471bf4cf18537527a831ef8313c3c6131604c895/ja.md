```
XPRScreateprob(f, path)
```

`XPRSprob` インスタンスを作成し、`f` を実行し、`XPRSprob` インスタンスを解放します。`f` がエラーで終了しても、インスタンスは解放されます。

`f` : 実行する関数

`path` : これが `nothing` でない場合、関数はそのパスで Xpress を初期化します（`XPRSinit` を参照）し、`XPRSprob` インスタンスを作成します。`XPRSprob` インスタンスが破棄されると、Xpress は解放されます。

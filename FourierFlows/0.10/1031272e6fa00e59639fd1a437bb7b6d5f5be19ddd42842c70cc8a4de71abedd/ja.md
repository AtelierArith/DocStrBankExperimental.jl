```
Diagnostic(calc, prob; freq=1, nsteps=100, ndata=ceil(Int, (nsteps+1)/freq))
```

`calc(prob)`の結果を`freq`の頻度で保存する診断を構築します。

# キーワード

  * `freq`: 診断は`freq`ステップごとに保存されます。
  * `nsteps`: 問題の総ステップ数。
  * `ndata`: 保存される診断の数。

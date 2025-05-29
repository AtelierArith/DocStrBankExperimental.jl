```
TimeSequence(f, ev, times)
TimeSequence(f, ev_iter)
```

進化イテレータ `ev` を反復処理し、各瞬間に関数 `f` を適用することで TimeSequence を構築します。

## 引数

  * `f`: 瞬間を受け取り、値を返す関数。進化の各瞬間にこの関数が適用されます。
  * `ev`: `Evolution` オブジェクト。
  * `times`: 関数を評価する時間の範囲。
  * `ev_iter`: 瞬間を生成する進化イテレータ。`ev(times)` のように考えてください。

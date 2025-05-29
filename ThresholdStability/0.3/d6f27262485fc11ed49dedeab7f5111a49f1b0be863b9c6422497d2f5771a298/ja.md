```
sosbound_γ(s::StateDepDiscreteSwitchedLinearSystem, d)
```

最小値 $γ$ を計算します。これは、二次和プログラムが実行可能であるためのものです。

# キーワード

  * `optimizer=...`: SDPソルバーを選択します。デフォルトのソルバーはCSDPです。
  * `tol=...`: 許容誤差を設定します。デフォルトは `tol=1e-5` です。
  * `verbose=...`: 計算プロセス中に報告される詳細レベルを設定します。デフォルトは `verbose=0` です。
  * `initstep=...`: 初期ステップサイズを設定します。デフォルト値は `initstep=1.1` です。

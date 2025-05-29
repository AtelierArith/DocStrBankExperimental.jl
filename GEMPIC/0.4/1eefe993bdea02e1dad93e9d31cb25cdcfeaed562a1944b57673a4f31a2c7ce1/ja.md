```
TimeHistoryDiagnostics( particle_group, maxwell_solver, 
                        kernel_smoother_0, kernel_smoother_1 )
```

診断を保存してプロットするためのコンテキスト

  * `particle_group` : 粒子データ
  * `maxwell_solver` : マクスウェルソルバー
  * `kernel_smoother_0` : メッシュ結合オペレーター
  * `kernel_smoother_1` : メッシュ結合オペレーター
  * `data` : 時間履歴値を含むDataFrame

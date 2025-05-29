```
empirical_gramian()
```

制御可能性または観測可能性グラミアンの計算のための関数。

# 参考文献

[1] M. Tahavori and A. Hasan, “Fault recoverability for nonlinear systems with application to fault tolerant control of UAVs,” Aerosp. Sci. Technol., vol. 107, p. 106282, 2020, doi: 10.1016/j.ast.2020.106282. [2] C. Himpe, “emgr-The empirical Gramian framework,” Algorithms, vol. 11, no. 7, pp. 1–27, 2018, doi: 10.3390/a11070091.

# 注意事項

  * f = (x, u, p, t) の関数
  * g = (x, u, p, t) の関数
  * pr = パラメータベクトル、各列 i は1つのパラメータサンプル
  * xs = 定常状態および名目初期状態 x_0
  * us = 定常状態入力
  * opt = :c は制御可能性グラミアン、:o は観測可能性グラミアン

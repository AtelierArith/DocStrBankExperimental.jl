```
Launcher(arch, grid; outer_width=nothing)
```

入力パラメータに基づいて構成された `Launcher` オブジェクトを構築します。

## 引数:

  * `arch`: 関連するアーキテクチャ。
  * `grid`: 計算ドメインを定義するグリッド。
  * `outer_width`: 外幅を指定するオプションのパラメータ。

!!! warning
    最後の次元 N の worksize は、最後の外幅 W[N] のみを考慮し、N-1 は W[N] と W[N-1] を使用し、N-2 は W[N]、W[N-1]、および W[N-2] を使用します。


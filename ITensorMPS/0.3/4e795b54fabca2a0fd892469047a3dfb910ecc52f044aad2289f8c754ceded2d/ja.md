```
DMRGObserver(;energy_tol=0.0,
              minsweeps=2,
              energy_type=Float64)
```

エネルギーの許容誤差を提供し、実行する必要がある最小スイープ数を指定してDMRGObserverを構築します。

オプションのキーワード引数：

  * energy_tol: 1回のスイープから次のスイープへのエネルギーがこの量以上に変化しなくなった場合、現在のスイープの後に停止します
  * minsweeps: 少なくともこの数のスイープを実行します
  * energy_type: 各ステップでエネルギーを保存する際に使用する型

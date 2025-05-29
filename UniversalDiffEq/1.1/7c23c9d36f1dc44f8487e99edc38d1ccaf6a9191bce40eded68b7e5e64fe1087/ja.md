```
equilibrium_and_stability(UDE::MultiUDE,site,X,lower,upper;t=0,Ntrials=100,tol=10^-3)
```

UDEモデルの上限と下限の間のすべての平衡点を見つけようとし、次に安定性を分析するために支配的な固有値の実成分を返します。

...

# kwargs

  * t = 0: UDEモデルが評価される時点で、時間に依存するUDEにのみ関連します。
  * Ntrials = 100: 根探索アルゴリズムの初期化の数。
  * tol = 10^-3: 新しい平衡が保持されるのに十分に異なるポイント間の閾値ユークリッド距離。

...

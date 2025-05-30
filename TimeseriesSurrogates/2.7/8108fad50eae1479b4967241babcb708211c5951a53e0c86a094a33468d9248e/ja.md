```
IAAFT(M = 100, tol = 1e-6, W = 75)
```

反復調整された振幅調整フーリエ変換サロゲート[^SchreiberSchmitz1996]。

IAAFTサロゲートは、元のデータの振幅分布を保持しつつ、同じ線形相関または周期グラムを持ちますが、反復調整を通じてAAFTに対して改善されています（最大`M`ステップまで実行されます）。反復調整中、元の信号とサロゲートの周期グラムは粗いグレイン化され、パワーは`W`の等幅周波数ビンで平均化されます。反復手順は、周期グラム間の相対偏差が`tol`未満になるか、`M`に達するまで終了します。

IAAFTは、AAFTと同様に、データが線形ガウス過程の単調非線形変換から来ているという帰無仮説をテストするために使用できます。

[^SchreiberSchmitz1996]: T. Schreiber; A. Schmitz (1996). "Improved Surrogate Data for Nonlinearity Tests". [Phys. Rev. Lett. 77 (4)](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.77.635)

```
SVDD_train(K, nu)
```

カーネル行列 K と最大可能な外れ値の割合 `nu` を与えて、1クラスのサポートベクターマシンモデル（すなわち、サポートベクターデータ記述）をトレーニングします。モデルオブジェクト（`svdd_model`）を返します。LIBSVMが必要です。

Tax, D. M. J., & Duin, R. P. W. (1999). Support vector domain description. Pattern Recognition Letters, 20, 1191–1199. Schölkopf, B., Williamson, R. C., & Bartlett, P. L. (2000). New Support Vector Algorithms. Neural Computation, 12, 1207–1245.

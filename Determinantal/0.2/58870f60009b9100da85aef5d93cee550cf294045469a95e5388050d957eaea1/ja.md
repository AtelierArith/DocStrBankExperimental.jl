```
 marginal_kernel(L::AbstractLEnsemble)
```

DPPの周辺カーネルKを計算して返します。DPPの周辺カーネルは、包含確率を求めるために使用できる(n x n)行列です。固定されたインデックスのセットindに対して、DPPからのサンプルにindが含まれる確率はdet(K[ind,ind])に等しいです。

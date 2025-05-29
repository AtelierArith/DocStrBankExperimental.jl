```
FISTA(x0,y,Hop,PARAM,mu,Nit)
```

FISTA: 高速反復収縮閾値アルゴリズムを介して l2-l1 問題を解決します。線形演算子 H とその随伴 H' が与えられたとき、アルゴリズムは J = ||H x - y||*2^2 + mu ||x||*1 を最小化します。ここで H は Hop にカプセル化された線形演算子です。

# 引数

  * `y`:データ
  * `Hop`:線形演算子
  * `PARAM`:Hop とその随伴を実行するためのパラメータ
  * `mu`:トレードオフパラメータ
  * `x0`:x のサイズを取得するための初期解

参考文献: Beck and Teboulle, 2009, A Fast Iterative Shrinkage-Thresholding Algorithm for Linear Inverse Problems∗ SIAM J. Imaging Science, Vol 2 (1), 183-202

```
project(B::VectorBundle, p)
```

ベクトルバンドル `B` の周囲空間から多様体 `B.fiber`（記号 $\mathcal M$）上の点 `p` をベクトルバンドルに射影します。

表記法:

  * 点 $p = (x_p, V_p)$ は、$x_p$ が $\mathcal M$ の周囲空間に属し、$V_p$ がベクトルバンドル $B$ のファイバー $F=π^{-1}(\{x_p\})$ の周囲空間に属します。ここで、$π$ はそのベクトルバンドル $B$ の標準射影です。

射影は、点 $x_p$ を多様体 $\mathcal M$ に射影し、その後ベクトル $V_p$ を接空間 $T_{x_p}\mathcal M$ に射影することによって計算されます。

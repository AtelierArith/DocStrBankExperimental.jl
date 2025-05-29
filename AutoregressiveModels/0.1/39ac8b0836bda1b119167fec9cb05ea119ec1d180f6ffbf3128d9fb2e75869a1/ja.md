```
VARProcess(B::AbstractMatrix, B0=nothing; copy::Bool=false)
```

ベクトル自己回帰過程 $Y_t$ を次のように定義します。

$$
Y_t = B_0 + \sum_{l=1}^p B_l Y_{t-l} + \ε_t
$$

ここで、自己回帰係数 $\{\B_l\}_l$ は行列 `B` に列ごとに集められ、オプションの切片 $B_0$ はベクトル `B0` にあります。

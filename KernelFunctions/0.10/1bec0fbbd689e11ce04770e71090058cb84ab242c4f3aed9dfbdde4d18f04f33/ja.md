```
nystrom(k::Kernel, X::AbstractVector, r::Real)
```

データベクトル `X` の平方カーネル行列のニーストローム近似の因子分解を、カーネル `k` に対してサンプル比 `r` を使用して計算します。ニーストローム因子分解を格納する `NystromFact` 構造体を返します。この因子分解は次の条件を満たします：

$$
\mathbf{K} \approx \mathbf{C}^{\intercal}\mathbf{W}\mathbf{C}
$$

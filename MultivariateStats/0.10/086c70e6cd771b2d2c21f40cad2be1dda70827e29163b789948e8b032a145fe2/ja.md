```
ldacov(C, μp, μn)
```

与えられた共分散行列 `C` と両方の平均ベクトル `μp` & `μn` に基づいて LDA を実行します。タイプ [`LinearDiscriminant`](@ref) の線形判別関数を返します。

*パラメータ*

  * `C`: プールされた共分散行列 (*すなわち* $(\mathbf{C}_p + \mathbf{C}_n)/2$)
  * `μp`: 正のクラスの平均ベクトル。
  * `μn`: 負のクラスの平均ベクトル。

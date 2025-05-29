```
empirical_interpolation(a::Projection) -> (AbstractVector,AbstractMatrix)
```

`a`のEIMを計算します。出力は次のとおりです：

  * 補間行列インデックスのリストに対応する整数のベクトル `i`
  * 行列 `Φi = view(Φ,i)`、ここで `Φ = get_basis(a)`。この量は、補間行のセット `i` に対する制限された基底を表します。

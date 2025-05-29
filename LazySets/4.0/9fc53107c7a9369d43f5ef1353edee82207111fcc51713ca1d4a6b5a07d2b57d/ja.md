```
linear_map(M::AbstractMatrix, ilm::InverseLinearMap)
```

遅延逆線形写像の線形写像を返します。

### 入力

  * `M`   – 行列
  * `ilm` – 逆線形写像

### 出力

遅延逆線形写像の線形写像を表す集合。

### 注意事項

この実装は非効率的です。なぜなら、`InverseLinearMap` が避けるべき具体的な逆行列 $M$ を計算するからです。

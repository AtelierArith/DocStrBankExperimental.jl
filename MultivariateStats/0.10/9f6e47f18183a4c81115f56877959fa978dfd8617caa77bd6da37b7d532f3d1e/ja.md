```
projection(M::KernelPCA)
```

投影行列（サイズ $n \times p$）を返します。投影行列の各列は固有ベクトルに対応し、$n$ は観測の数です。

主成分は対応する固有値の降順に配置されています。

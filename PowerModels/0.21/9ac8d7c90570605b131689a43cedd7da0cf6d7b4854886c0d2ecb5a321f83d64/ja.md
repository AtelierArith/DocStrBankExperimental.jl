ブランチフローモデルの線形近似。

この実装はブランチフローモデルの二次円錐緩和に基づいていますが、電流の大きさの二乗に関連する有効および無効損失項を無視するため、電力フロー方程式は線形になります。フローの制約は依然として二次円錐です。

```
@article{Baran1989OptimalSystems,
    title = {{Optimal capacitor placement on radial distribution systems}},
    year = {1989},
    journal = {IEEE Transactions on Power Delivery},
    author = {Baran, Mesut E. and Wu, Felix F.},
    number = {1},
    pages = {725--734},
    volume = {4},
    doi = {10.1109/61.19265},
    issn = {19374208}
}
```

名前に `_bf` を含む問題定式に適用可能です。

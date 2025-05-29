```
selectmodel(path::RegularizationPath, select::SegSelect)
```

選択された正則化パスのセグメントを表すLinearModelまたはGeneralizedLinearModelを返します。

# 例

```julia
selectmodel(path, MinBIC())            # BIC最小化モデル
selectmodel(path, MinCVmse(path, 5))   # 5分割CV mse最小化モデル
```

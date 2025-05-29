```
kabsch(from_points => to_points, w=ones(npoints); scale::Bool=false, svd=LinearAlgebra.svd) → trans
```

`from_points`を`to_points`に最小二乗法的に整列させる剛体変換（または`scale=true`の場合は類似変換）を計算します。

各点の非負の重み`w`をオプションで指定できます。重みのデフォルト値は各点に対して1です。

微分可能性のために、`svd = GenericLinearAlgebra.svd`または他の微分可能な特異値分解を使用してください。

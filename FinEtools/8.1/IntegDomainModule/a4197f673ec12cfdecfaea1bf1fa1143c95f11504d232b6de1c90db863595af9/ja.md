```
integrationdata(
    self::IntegDomain,
    integration_rule::IR,
) where {IR<:AbstractIntegRule}
```

与えられた数値的な積分ルールに必要なデータを計算します。

与えられた積分領域に対して、数値積分に必要な量を計算します。積分ルールは、必ずしも元々積分領域に関連付けられたものである必要はありません。

# 戻り値

`npts`, `Ns`, `gradNparams`, `w`, `pc` = 積分点の数、積分点での基底関数の値の配列、パラメトリック座標に関する基底関数の勾配の配列、重みの配列、および積分点の位置の配列。

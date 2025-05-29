```
vif(m::RegressionModel)
```

分散膨張係数 (VIF) を計算します。

[VIF](https://en.wikipedia.org/wiki/Variance_inflation_factor) は、複数のパラメータを持つモデルにおけるパラメータの推定値の分散の増加を、単一のパラメータのみを含むモデルにおけるパラメータの推定値の分散に対して測定します。

他に [`gvif`](@ref) も参照してください。

!!! warning
    このメソッドは、（数値的に）完全な多重共線性、すなわちランク欠損がある場合に失敗します。その場合、VIF は特に有益ではありません。


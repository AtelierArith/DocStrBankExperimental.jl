```
gvif(model::RegressionModel; scale=false)
```

一般化分散膨張係数 (GVIF) を計算します。

`scale=true` の場合、各 GVIF は予測子に関連する自由度の数でスケーリングされます: $GVIF^(1 / (2*df))$。

切片を除く各項に対して計算された膨張係数のベクトルを返します。言い換えれば、対応する係数は `termnames(m)[2:end]` です。

[GVIF](https://doi.org/10.2307/2290467) は、複数のパラメータを持つモデルにおけるパラメータの推定値の分散の増加を、単一のパラメータのみを含むモデルにおけるパラメータの推定値の分散に対して測定します。連続的な数値予測子に対しては、GVIF は VIF と同じですが、カテゴリカル予測子に対しては、GVIF はカテゴリカル予測子に関連するコントラストコーディングされた係数の全体のグループに対して単一の数値を提供します。

[`termnames`](@ref) や [`vif`](@ref) も参照してください。

!!! warning
    このメソッドは、（数値的に）完全な多重共線性、すなわちランク欠損がある場合に失敗します。その場合、VIF は特に有益ではありません。


# 参考文献

Fox, J., & Monette, G. (1992). Generalized Collinearity Diagnostics. Journal of the American Statistical Association, 87(417), 178. doi:10.2307/2290467

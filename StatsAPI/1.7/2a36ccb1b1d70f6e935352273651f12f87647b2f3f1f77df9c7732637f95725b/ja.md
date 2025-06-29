```
gvif(m::RegressionModel; scale=false)
```

一般化分散膨張係数（GVIF）を計算します。

`scale=true` の場合、各 GVIF は予測子に関連する係数の自由度でスケーリングされます: $GVIF^(1 / (2*df))$。

[GVIF](https://doi.org/10.2307/2290467) は、複数のパラメータを持つモデルにおける（グループの）パラメータ推定の分散の増加を、単一のパラメータのみを含むモデルにおけるパラメータ推定の分散に対して測定します。連続的な数値予測子に対して、GVIF は VIF と同じですが、カテゴリカル予測子に対しては、GVIF はカテゴリカル予測子に関連するコントラストコーディングされた係数の全体のグループに対して単一の数値を提供します。

[`vif`](@ref) も参照してください。

## 参考文献

Fox, J., & Monette, G. (1992). Generalized Collinearity Diagnostics. Journal of the American Statistical Association, 87(417), 178. doi:10.2307/2290467

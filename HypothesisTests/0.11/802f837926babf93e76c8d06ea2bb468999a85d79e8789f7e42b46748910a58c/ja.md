```
KSampleADTest(xs::AbstractVector{<:Real}...; modified = true, nsim = 0)
```

$$
k
$$

-サンプルアンダーソン–ダーリング検定を実行し、$k$ベクトル`xs`のデータが同じ分布から来ているという帰無仮説に対して、サンプルが異なる分布から来ているという対立仮説を検証します。

`modified`パラメータは、観測値がすべて一致しないサンプルのための修正された検定計算を有効にします。

`nsim`が0（デフォルト）の場合、p値の漸近的計算が使用されます。0より大きい場合、$k$サンプルのプールデータの`nsim`ランダム分割を生成し、各分割のAD統計量を評価し、観測値以上のシミュレーション値の割合を計算することによってp値の推定が行われます。この割合がp値の推定値として報告されます。

実装: [`pvalue`](@ref)

# 参考文献

  * F. W. Scholz と M. A. Stephens, K-Sample Anderson-Darling Tests, Journal of the American Statistical Association, Vol. 82, No. 399. (1987年9月), pp. 918-924.

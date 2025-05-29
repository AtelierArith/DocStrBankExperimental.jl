```
neglected_lag(τmax)
```

動的 `1/(s*τ + 1)` を無視することから生じる不確実性を表す乗法的重みを返します。ここで、`τ ≤ τmax` です。「Multivariable Feedback Control: Analysis and Design」第7.4.5章を参照してください。

[`gain_and_delay_uncertainty`](@ref) および [`neglected_delay`](@ref) も参照してください。

# 例:

```julia
a = 10
P = ss([0 a; -a 0], I(2), [1 a; -a 1], 0) # プラント
W0 = neglected_lag(0.05) |> ss # 重み
W = I(2) + W0*I(2) * uss([δc(), δc()]) # W0 によって周波数で重み付けされた対角の実不確実性を作成
Ps = P*W # 不確実なプラント
Psamples = rand(Ps, 100) # プロット用に不確実なプラントをサンプリング
w = exp10.(LinRange(-1, 3, 300)) # 周波数ベクトル
sigmaplot(Psamples, w)
```

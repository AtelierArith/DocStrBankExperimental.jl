```
neglected_delay(Lmax)
```

動的 `exp(-s*L)` を無視することから生じる不確実性を表す乗法的重みを返します。ただし、`L ≤ Lmax` です。「マルチバリアブルフィードバック制御: 分析と設計」第7.4.5章

[`gain_and_delay_uncertainty`](@ref) および [`neglected_lag`](@ref) も参照してください。

# 例:

```julia
a = 10
P = ss([0 a; -a 0], I(2), [1 a; -a 1], 0) # プラント
W0 = neglected_delay(0.005) |> ss # 重み
W = I(2) + W0*I(2) * uss([δc(), δc()]) # W0 によって周波数で重み付けされた対角の実不確実性を作成
Ps = P*W # 不確実なプラント
Psamples = rand(Ps, 500) # プロット用に不確実なプラントをサンプリング
w = exp10.(LinRange(-1, 3, 300)) # 周波数ベクトル
bodeplot(Psamples, w)
```

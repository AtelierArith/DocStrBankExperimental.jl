```
gain_and_delay_uncertainty(kmin, kmax, Lmax)
```

動的 `k*exp(-s*L)` を無視することから生じる不確実性を表す乗法的重みを返します。ここで、`k ∈ [kmin, kmax]` および `L ≤ Lmax` です。この重みはやや楽観的であり、より正確な重みの表現は「Multivariable Feedback Control: Analysis and Design」の式 (7.27) に示されています。

また、[`neglected_lag`](@ref) および [`neglected_delay`](@ref) も参照してください。

# 例:

```julia
a = 10
P = ss([0 a; -a 0], I(2), [1 a; -a 1], 0) # プラント
W0 = gain_and_delay_uncertainty(0.5, 2, 0.005) |> ss # 重み
W = I(2) + W0*I(2) * uss([δc(), δc()]) # W0 によって周波数で重み付けされた対角の実不確実性を作成
Ps = P*W # 不確実なプラント
Psamples = rand(Ps, 500) # プロット用に不確実なプラントをサンプリング
w = exp10.(LinRange(-1, 3, 300)) # 周波数ベクトル
bodeplot(Psamples, w)
```

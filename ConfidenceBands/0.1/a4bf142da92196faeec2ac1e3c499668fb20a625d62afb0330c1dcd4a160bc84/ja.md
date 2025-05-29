```
confint(cb::SuptCVBootBand, θ0::AbstractVector, draws::AbstractMatrix; level::Real=0.9)
```

モンティエル・オレアとプラグボルグ・ミュラー（2019）の付録に基づくクリティカルバリューに基づくブートストラップ実装を用いて、sup-t信頼帯を計算します。`θ0`は、バンドの中間点として使用される点推定値のベクトルです。ブートストラップの`draws`は、同じドローからの点推定値のベクトルが各列にある行列である必要があります。下限と上限に加えて、クリティカルバリューが3番目のオブジェクトとして返されます。

# 参考文献

  * Montiel Olea, José Luis and Mikkel Plagborg-Møller. 2019. "Simultaneous Confidence Bands: Theory, Implementation, and an Application to SVARs." Journal of Applied Econometrics 34 (1): 1-17.

```
BIC(DM::DataModel, θ::AbstractVector) -> Real
```

パラメータ構成 $\theta$ に基づいてベイズ情報基準を計算します。$\mathrm{BIC} = \mathrm{ln}(N) \cdot \mathrm{length}(\theta) -2 \, \ell(\mathrm{data} \, | \, \theta)$ であり、ここで $N$ はデータポイントの数です。

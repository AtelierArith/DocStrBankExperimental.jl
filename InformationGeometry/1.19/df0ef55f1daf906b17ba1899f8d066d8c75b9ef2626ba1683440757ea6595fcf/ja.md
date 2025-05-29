```
AICc(DM::DataModel, θ::AbstractVector) -> Real
```

小さいサンプルサイズの場合に、AICがパラメータが多すぎるモデル（すなわち、過剰適合）を選択するのを防ぐための補正項が追加されたAkaike情報量基準を計算します。 $\mathrm{AICc} = \mathrm{AIC} + \frac{2\mathrm{length}(\theta)^2 + 2 \mathrm{length}(\theta)}{N - \mathrm{length}(\theta) - 1}$ ここで、$N$はデータポイントの数です。AICが情報損失の一次推定を構成するのに対し、AICcは二次推定を構成します。ただし、この特定の補正項はモデルが**線形パラメータ化**されていることを前提としています。

```
AIC(DM::DataModel, θ::AbstractVector) -> Real
```

パラメータ構成 $\theta$ に基づいて赤池情報量基準を計算します。$\mathrm{AIC} = 2 \, \mathrm{length}(\theta) -2 \, \ell(\mathrm{data} \, | \, \theta)$。AICの値が低いほど、関連するモデル関数が正しい可能性が高くなります。線形パラメータ化されたモデルと小さなサンプルサイズの場合は、より正確なAICcを使用することをお勧めします。

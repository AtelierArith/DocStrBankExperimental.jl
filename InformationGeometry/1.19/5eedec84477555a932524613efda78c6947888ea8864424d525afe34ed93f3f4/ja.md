```
FisherMetric(DM::DataModel, θ::AbstractVector{<:Number})
```

`DataModel`とパラメータ構成$\theta$を与えられたときに、尤度$L(\mathrm{data} \, | \, \theta)$が多変量正規分布であるという仮定の下で、フィッシャー計量$g$を計算します。

$$
g_{ab}(\theta) \coloneqq -\int_{\mathcal{D}} \mathrm{d}^m y_{\mathrm{data}} \, L(y_{\mathrm{data}} \,|\, \theta) \, \frac{\partial^2 \, \mathrm{ln}(L)}{\partial \theta^a \, \partial \theta^b} = -\mathbb{E} \bigg( \frac{\partial^2 \, \mathrm{ln}(L)}{\partial \theta^a \, \partial \theta^b} \bigg)
$$

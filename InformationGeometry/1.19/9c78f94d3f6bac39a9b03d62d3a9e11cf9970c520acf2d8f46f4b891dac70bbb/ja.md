```
EmbeddingMap(DM::AbstractDataModel, θ::AbstractVector{<:Number}) -> Vector
```

モデルの集団予測のベクトルを返します。これは、x値とパラメータ構成 $\theta$ で評価されたものです。

```
h(\theta) \coloneqq \big(y_\mathrm{model}(x_1;\theta),...,y_\mathrm{model}(x_N;\theta)\big) \in \mathcal{D}
```

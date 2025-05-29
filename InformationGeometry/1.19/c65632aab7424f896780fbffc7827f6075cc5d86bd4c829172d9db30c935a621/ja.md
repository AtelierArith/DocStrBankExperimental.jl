```
TotalLeastSquares(DM::DataModel, initialθ::AbstractVector=MLE(DM), start::AbstractVector=[xdata(DM);initialp]; tol::Real=1e-13, kwargs...) -> Vector
```

x値の不確実性を考慮してフィットの精度を向上させる実験的な機能です。x値とパラメータの連結ベクトルを返します。x値とy値の不確実性は正規分布、すなわちガウス分布であると仮定します！

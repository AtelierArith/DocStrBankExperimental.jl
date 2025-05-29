```
TransformedRegularization(reg, trafo)
```

ネストされた正則化項で、`z = trafo * x` に対して `prox!` または `norm` を適用し、（インプレースで）`x = adjoint(trafo) * z` を返します。

# 例

```julia
julia> core = L1Regularization(0.8)
L1Regularization{Float64}(0.8)

julia> wop = WaveletOp(Float32, shape = (32,32));

julia> reg = TransformedRegularization(core, wop);

julia> prox!(reg, randn(32*32)); # ウェーブレット領域でソフトしきい値処理を適用
```

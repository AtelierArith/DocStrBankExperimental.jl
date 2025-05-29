```
TruncatedConjugateGradientState <: AbstractHessianSolverState
```

Steihaug-Tointの切り捨て共役勾配法について説明します。

# フィールド

初期化時にパラメータを省略できる場合は、デフォルト値が括弧内に示されています。

  * `Y`:                   (`zero_vector(M,p)`) 現在の反復値で、他の内部接線ベクトルフィールドにも使用される型です。
  * `stop`:                [`StoppingCriterion`](@ref)。
  * `X`:                   勾配 $\operatorname{grad}f(p)$`
  * `δ`:                   共役勾配探索方向
  * `θ`:                   (`1.0`) 1+θは超線形収束目標率です。
  * `κ`:                   (`0.1`) 線形収束目標率です。
  * `trust_region_radius`: (`injectivity_radius(M)/4`) 信頼領域の半径
  * `residual`:            モデルの勾配 $m(Y)$
  * `randomize`:           (`false`)
  * `project!`:            (`copyto!`) 数値的安定性のため、各反復後に接線空間に投影することが可能です。デフォルトでは、これは単にコピーするだけです。

# 内部フィールド

  * `Hδ`, `HY`:                 `δ`および`Y`に適用されたヘッセ行列の一時的な結果。
  * `δHδ`, `YPδ`, `δPδ`, `YPδ`: ヘッセ行列との一時的な内積および前処理された内積。
  * `z`:                        前処理された残差
  * `z_r`:                      残差と`z`の内積

# コンストラクタ

```
TruncatedConjugateGradientState(TpM::TangentSpace, Y=rand(TpM); kwargs...)
```

# 参照

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref) ```

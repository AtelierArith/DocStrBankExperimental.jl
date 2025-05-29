```
DeepGalerkin(in_dims::Int, out_dims::Int, modes::Int, L::Int, activation1::Function,
    activation2::Function, out_activation::Function, strategy::AbstractTrainingStrategy;
    kwargs...)
```

## 引数:

  * `in_dims`: 入力次元の数 = (空間次元 + 1)。
  * `out_dims`: 出力次元の数。
  * `modes`: LSTMタイプの層の幅。
  * `L`: LSTMタイプの層の数。
  * `activation1`: LSTMタイプの層で使用される活性化関数。
  * `activation2`: LSTMタイプの層の出力に使用される活性化関数。
  * `out_activation`: ネットワークの出力に使用される活性化関数。
  * `kwargs`: [`PhysicsInformedNN`](@ref) にスプラットされる追加の引数。

## 例

```julia
discretization = DeepGalerkin(2, 1, 30, 3, tanh, tanh, identity, QuasiRandomTraining(4_000))
```

## 参考文献

Sirignano, Justin and Spiliopoulos, Konstantinos, "DGM: A deep learning algorithm for solving partial differential equations", Journal of Computational Physics, Volume 375, 2018, Pages 1339-1364, doi: https://doi.org/10.1016/j.jcp.2018.08.029

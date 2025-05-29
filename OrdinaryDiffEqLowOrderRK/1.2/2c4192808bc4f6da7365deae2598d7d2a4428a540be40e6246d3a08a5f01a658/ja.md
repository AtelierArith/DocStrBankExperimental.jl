```julia
FRK65(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False(),
        omega = 0.0)
```

明示的ルンゲ-クッタ法。ゼロ散逸の6次ルンゲ-クッタ法。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。
  * `omega`: 周期的な位相推定、

正確であれば、この方法はゼロの数値散逸をもたらします。

## 参考文献

@article{medvedev2018fitted, title={Fitted modifications of Runge-Kutta pairs of orders 6 (5)}, author={Medvedev, Maxim A and Simos, TE and Tsitouras, Ch}, journal={Mathematical Methods in the Applied Sciences}, volume={41}, number={16}, pages={6184–6194}, year={2018}, publisher={Wiley Online Library}}

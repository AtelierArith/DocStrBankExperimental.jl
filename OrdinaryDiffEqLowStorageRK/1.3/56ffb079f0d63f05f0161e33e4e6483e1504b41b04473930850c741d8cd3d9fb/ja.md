```julia
SHLDDRK_2N(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
             step_limiter! = OrdinaryDiffEq.trivial_limiter!,
             thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。計算音響のための低い消散と分散のルンゲ-クッタスキーム

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 内部ブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

@article{stanescu19982n,     title={2N-storage low dissipation and dispersion Runge-Kutta schemes for computational acoustics},     author={Stanescu, D and Habashi, WG},     journal={Journal of Computational Physics},     volume={143},     number={2},     pages={674–681},     year={1998},     publisher={Elsevier}}

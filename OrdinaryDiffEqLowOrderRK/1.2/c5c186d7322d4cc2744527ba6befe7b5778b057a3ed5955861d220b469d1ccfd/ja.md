```julia
Alshina3(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
           step_limiter! = OrdinaryDiffEq.trivial_limiter!,
           thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。最適なパラメータを持つ3次、3段階の方法。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: Juliaが複数のスレッドで起動されたときに、適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、または複数のスレッドを使用するべきかを決定します（`thread = OrdinaryDiffEq.True()`）。

## 参考文献

@article{Alshina2008,     doi = {10.1134/s0965542508030068},     url = {https://doi.org/10.1134/s0965542508030068},     year = {2008},     month = mar,     publisher = {Pleiades Publishing Ltd},     volume = {48},     number = {3},     pages = {395–405},     author = {E. A. Alshina and E. M. Zaks and N. N. Kalitkin},     title = {Optimal first- to sixth-order accurate Runge-Kutta schemes},     journal = {Computational Mathematics and Mathematical Physics}     }

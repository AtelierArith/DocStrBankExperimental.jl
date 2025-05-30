```julia
Alshina6(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
           step_limiter! = OrdinaryDiffEq.trivial_limiter!,
           thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。6次、7段階の方法で最適なパラメータを持つ。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 内部ブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

@article{Alshina2008,     doi = {10.1134/s0965542508030068},     url = {https://doi.org/10.1134/s0965542508030068},     year = {2008},     month = mar,     publisher = {Pleiades Publishing Ltd},     volume = {48},     number = {3},     pages = {395–405},     author = {E. A. Alshina and E. M. Zaks and N. N. Kalitkin},     title = {最適な1次から6次までの精度を持つルンゲ-クッタスキーム},     journal = {Computational Mathematics and Mathematical Physics}     }

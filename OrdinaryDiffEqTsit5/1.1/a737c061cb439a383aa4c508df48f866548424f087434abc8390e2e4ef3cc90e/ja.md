```julia
Tsit5(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False())
```

明示的ルンゲ・クッタ法。埋め込まれた誤差推定器を持つ5次の明示的ルンゲ・クッタ法で、Tsitourasのものです。自由な4次補間子。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列で行われるべきか (`thread = OrdinaryDiffEq.False()`) または複数のスレッドを使用するべきか (`thread = OrdinaryDiffEq.True()`) を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

@article{tsitouras2011runge,     title={Runge–Kutta pairs of order 5 (4) satisfying only the first column simplifying assumption},     author={Tsitouras, Ch},     journal={Computers \& Mathematics with Applications},     volume={62},     number={2},     pages={770–775},     year={2011},     publisher={Elsevier}     }

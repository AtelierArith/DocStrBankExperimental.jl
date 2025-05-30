```julia
RDPK3Sp510(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
             step_limiter! = OrdinaryDiffEq.trivial_limiter!,
             thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。圧縮性流体力学のスペクトル要素離散化のために設計された、埋め込まれた誤差推定器を持つ5次、10段階の方法です。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 内部ブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

Ranocha, Dalcin, Parsani, Ketcheson (2021)     自動ステップサイズ制御を持つ最適化されたルンゲ-クッタ法     [arXiv:2104.06836](https://arxiv.org/abs/2104.06836)

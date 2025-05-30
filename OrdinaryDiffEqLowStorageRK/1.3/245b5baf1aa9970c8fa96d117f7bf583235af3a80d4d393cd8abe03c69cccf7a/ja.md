```julia
RDPK3SpFSAL49(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
                step_limiter! = OrdinaryDiffEq.trivial_limiter!,
                thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。FSAL特性を使用した埋め込み誤差推定器を持つ4次、9段階の方法で、圧縮性流体力学のスペクトル要素離散化のために設計されています。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

Ranocha, Dalcin, Parsani, Ketcheson (2021)     自動ステップサイズ制御を持つ最適化ルンゲ-クッタ法     [arXiv:2104.06836](https://arxiv.org/abs/2104.06836)

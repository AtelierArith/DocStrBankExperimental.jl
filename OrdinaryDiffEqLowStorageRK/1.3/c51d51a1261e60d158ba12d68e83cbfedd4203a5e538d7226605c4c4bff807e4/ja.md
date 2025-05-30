```julia
ParsaniKetchesonDeconinck3S184(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
                                 step_limiter! = OrdinaryDiffEq.trivial_limiter!,
                                 thread = OrdinaryDiffEq.False())
```

明示的ルンゲ・クッタ法。 低ストレージ法 18段階、4次（3S）低ストレージスキームで、波動伝播問題に適用されるスペクトル差分法のために最適化されています。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

Parsani, Matteo, David I. Ketcheson, and W. Deconinck.     スペクトル差分法に適用される最適化された明示的ルンゲ–クッタスキーム。     SIAM Journal on Scientific Computing 35.2 (2013): A957-A986.     doi: https://doi.org/10.1137/120885899

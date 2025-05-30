```julia
RK4(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
      step_limiter! = OrdinaryDiffEq.trivial_limiter!,
      thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。標準的なルンゲ-クッタの4次法。全区間にわたる最大誤差を使用して適応ステッピングのための欠陥制御を使用します。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

@article{shampine2005solving,       title={Solving ODEs and DDEs with residual control},       author={Shampine, LF},       journal={Applied Numerical Mathematics},       volume={52},       number={1},       pages={113–127},       year={2005},       publisher={Elsevier}       }

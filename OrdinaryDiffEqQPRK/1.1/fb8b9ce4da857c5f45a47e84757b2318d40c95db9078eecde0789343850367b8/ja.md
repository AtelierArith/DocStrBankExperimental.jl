```julia
QPRK98(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
         step_limiter! = OrdinaryDiffEq.trivial_limiter!,
         thread = OrdinaryDiffEq.False())
```

明示的ルンゲ・クッタ法。四重精度計算に使用するための9(8)次のルンゲ–クッタペア

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: Juliaが複数のスレッドで起動されたときに、適切なCPU配列での内部ブロードキャストを直列（`thread = OrdinaryDiffEq.False()`）にするか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。

## 参考文献

Kovalnogov VN, Fedorov RV, Karpukhina TV, Simos TE, Tsitouras C. 四重精度計算に使用するための9 (8)次のルンゲ–クッタペア。数値アルゴリズム, 2023. doi: https://doi.org/10.1007/s11075-023-01632-8

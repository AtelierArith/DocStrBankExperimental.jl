```julia
PSRK3p5q4(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
            step_limiter! = OrdinaryDiffEq.trivial_limiter!,
            thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。4段階擬似シンプレクティック法。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 内部ブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

@article{Aubry1998,     author = {A. Aubry and P. Chartier},     journal = {BIT Numer. Math.},     title =  {擬似シンプレクティック {R}unge-{K}utta法},     year = {1998},     },     @article{Capuano2017,     title = {明示的 {R}unge–{K}uttaスキームによる非圧縮流のエネルギー保存特性の改善},     journal = {J. Comput. Phys.},     year = {2017},     author = {F. Capuano and G. Coppola and L. Rández and L. {de Luca}},}

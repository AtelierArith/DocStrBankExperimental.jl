```julia
DP8(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
      step_limiter! = OrdinaryDiffEq.trivial_limiter!,
      thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。ヘアーの8/5/3のドーマンド-プリンスルンゲ-クッタ法の適応。(7次の補間子)。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列で行われるべきか (`thread = OrdinaryDiffEq.False()`) または複数のスレッドを使用すべきか (`thread = OrdinaryDiffEq.True()`) を決定します。

## 参考文献

E. Hairer, S.P. Norsett, G. Wanner, (1993) Solving Ordinary Differential Equations I.     Nonstiff Problems. 2nd Edition. Springer Series in Computational Mathematics,     Springer-Verlag.

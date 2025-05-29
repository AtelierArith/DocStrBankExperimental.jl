```julia
SSPRK43(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
          step_limiter! = OrdinaryDiffEq.trivial_limiter!,
          thread = OrdinaryDiffEq.False())
```

明示的ルンゲ・クッタ法。三次、四段階の明示的強安定性保持（SSP）法。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

四段階の最適な三次明示SSP法は以下によって発見されました。

  * J. F. B. M. Kraaijevanger. "ルンゲ・クッタ法の収束性。" In: BIT Numerical Mathematics 31.3 (1991), pp. 482–528. [DOI: 10.1007/BF01933264](https://doi.org/10.1007/BF01933264).

埋め込み法は以下によって構築されました。

  * Sidafa Conde, Imre Fekete, John N. Shadid. "最適な明示的強安定性保持ルンゲ・クッタ法のための埋め込み誤差推定と適応的ステップサイズ制御。" [arXiv: 1806.08693](https://arXiv.org/abs/1806.08693)

効率的な実装（および最適化されたコントローラー）は以下によって開発されました。

  * Hendrik Ranocha, Lisandro Dalcin, Matteo Parsani, David I. Ketcheson (2021) 圧縮可能な計算流体力学のための自動ステップサイズ制御を持つ最適化されたルンゲ・クッタ法 [arXiv:2104.06836](https://arxiv.org/abs/2104.06836)

最適化(f, μ, σ, [method=sNES;options...])

関数 `f` を次のように最小化します：

```
`f` : 最適化する関数
    μ::Vector -> cost::Real
`μ` : 初期条件
    μ::Vector
`σ` : μに対する初期不確実性
    σ::{Real | Vector | Matrix}
`method` : xNES または sNES
    xNES = 指数進化戦略、非分離目的に対して高価だが強力
    sNES = 分離進化戦略、軽量で分離可能または非常に高次元の目的に対して非常に強力
`options` :
         ημ = μの学習率、
         ησ = 不確実性の学習率、
       atol = 不確実性に対する許容誤差（デフォルト 1e-8）、
    samples = 自然勾配近似を構築するために使用されるサンプル数、
    iterations = 繰り返しの上限（デフォルト 10^4）
```

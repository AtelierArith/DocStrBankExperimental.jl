```julia
struct VUMPS{F} <: MPSKit.Algorithm
```

均一行列積状態のための変分最適化アルゴリズムで、DMRGと行列積状態接線空間の概念の組み合わせに基づいています。

## フィールド

  * `tol::Float64`: 収束基準のための許容誤差
  * `maxiter::Int64`: 最大反復回数
  * `verbosity::Int64`: 表示される情報の量を設定する
  * `alg_gauge::Any`: `InfiniteMPS`のゲージに使用されるアルゴリズム
  * `alg_eigsolve::Any`: 固有値ソルバーに使用されるアルゴリズム
  * `alg_environments::Any`: MPS環境に使用されるアルゴリズム
  * `finalize::Any`: 各反復後に適用されるコールバック関数で、シグネチャは `finalize(iter, ψ, H, envs) -> ψ, envs`

## 参考文献

  * [Zauner-Stauber et al. Phys. Rev. B 97 (2018)](@cite zauner-stauber2018)
  * [Vanderstraeten et al. SciPost Phys. Lect. Notes 7 (2019)](@cite vanderstraeten2019)

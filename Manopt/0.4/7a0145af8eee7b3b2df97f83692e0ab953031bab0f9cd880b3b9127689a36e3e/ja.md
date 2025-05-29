```
NelderMead(M::AbstractManifold, f)
NelderMead(M::AbstractManifold, f, population::NelderMeadSimplex)
NelderMead(M::AbstractManifold, mco::AbstractManifoldCostObjective)
NelderMead(M::AbstractManifold, mco::AbstractManifoldCostObjective, population::NelderMeadSimplex)
```

コスト関数 $f:  \mathcal M$ に対するネルダー・ミード最小化問題を解きます。初期集団 `p` が指定されていない場合、ランダムな点の集合が選択されます。

このアルゴリズムはユークリッドのネルダー・ミード法から適応されています。詳細は [https://en.wikipedia.org/wiki/Nelder-Mead_method](https://en.wikipedia.org/wiki/Nelder-Mead_method) および [http://www.optimization-online.org/DB_FILE/2007/08/1742.pdf](http://www.optimization-online.org/DB_FILE/2007/08/1742.pdf) を参照してください。

# 入力

  * `M`:            多様体 $\mathcal M$
  * `f`:            最小化するコスト関数
  * `population`:   ($n+1$ `rand(M)`s) 多様体 `M` の次元 $n$ に対する初期集団 $n+1$ 点の集合

# オプション

  * `stopping_criterion`:        ([`StopAfterIteration`](@ref)`(2000) |`[`StopWhenPopulationConcentrated`](@ref)`()`) [`StoppingCriterion`](@ref)
  * `α`:                         (`1.`) 反射パラメータ ($α > 0$)
  * `γ`:                         (`2.`) 拡張パラメータ ($γ$)
  * `ρ`:                         (`1/2`) 縮小パラメータ、$0 < ρ ≤ \frac{1}{2}$,
  * `σ`:                         (`1/2`) 縮小係数、$0 < σ ≤ 1$
  * `retraction_method`:         (`default_retraction_method(M, typeof(p))`) 使用する引き戻し
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) 使用する逆引き戻し

およびデコレーター用に [`decorate_state!`](@ref) に渡されるもの。

!!! note
    ここで使用される多様体 `M` は、`mean(M, pts)` を提供するか、`Manifolds.jl` をロードしてその統計部分を使用する必要があります。


# 出力

得られた（近似的な）最小化点 $p^*$、詳細は [`get_solver_return`](@ref) を参照してください。

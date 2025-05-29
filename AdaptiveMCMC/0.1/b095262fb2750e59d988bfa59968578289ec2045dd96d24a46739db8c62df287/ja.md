```
out = adaptive_rwm(x0, log_p, n; kwargs)
```

初期状態ベクトル `x0` から、対数確率密度 `log_p` をターゲットにして `n` 回の反復を実行する一般的な適応ランダムウォークメトロポリスアルゴリズムで、適応的平行温度付けを含みます。

# 引数

  * `x0::Vector{<:AbstractFloat}`: 初期状態ベクトル
  * `log_p::Function`: 任意の状態ベクトルに対して対数確率密度値（加法定数を除く）を返す関数。
  * `n::Int`: 総反復回数

# キーワード引数

  * `algorithm::Symbol`: ランダムウォーク適応アルゴリズム; 現在の選択肢は `:ram`（デフォルト）、`:am`、`:asm`、`:aswam`、および `:rwm` です。（あるいは、algorithm が AdaptState のベクトルである場合、これは適応の初期状態として使用されます。）
  * `b::Int`: バーンインの長さ: `b`:番目のサンプルが最初に保存されるサンプルです。デフォルトは `⌊n/5⌋`
  * `thin::Int`: サンプリング間引き係数; `thin`:番目のサンプルのみが保存されます; デフォルトは `1`
  * `fulladapt::Bool`: バーンイン後に適応するかどうか; デフォルトは `true`
  * `Sp`: MCMCを再起動するために出力から保存された適応状態; デフォルトは `nothing`
  * `Rp`: MCMCを再起動するために出力から保存されたrng状態; デフォルトは `nothing`
  * `indp::Int`: MCMCを再起動するために保存された適応状態のインデックス; デフォルトは `0`
  * `rng::AbstractRNG`: 擬似乱数生成器; デフォルトは `Random.GLOBAL_RNG`
  * `q::Function`: ゼロ平均対称提案生成器（引数 `x` と `rng` を持つ）; デフォルトは `q=randn!(x, rng)`
  * `L::Int`: 平行温度付けレベルの数
  * `acc_sw::AbstractFloat`: レベルスワップ間の望ましい受け入れ率; デフォルトは `0.234`
  * `all_levels::Bool`: すべてのレベルの出力を保存するかどうか; デフォルトは `false`
  * `log_pr::Function`: 対数事前密度関数; デフォルトは `log_pr(x) = 0.0`。
  * `swaps::Symbol`: スワップ戦略の一つ: `:single`（デフォルト、ランダムに選ばれた単一スワップ） `:randperm`（ランダム順序でスワップ） `:sweep`（上または下にスイープ、ランダムに選択） `:nonrev`（Syed, Bouchard-Côté, Deligiannidis, Doucet における偶数/奇数サイトの交互スワップ、arXiv:1905.02939）
  * `progress::Union{Bool,Progress}`: 進行メーターが表示されるかどうか; デフォルトは `false`

`log_pr` が提供されている場合、`log_p(x)` は対数尤度（または同等に、対数ターゲットは `log_p(x) + log_pr(x)`）と見なされることに注意してください。温度付けは `log_p` のみに適用され、`log_pr` には適用されません。

出力 `out.X` にはシミュレーションされたサンプル（列ベクトル）が含まれます。`out.allX[k]` は `k>=2` の場合に高温の補助チェーンを含みます（要求された場合）。

# 例

```
log_p(x) = -.5*sum(x.^2)
o = adaptive_rwm(zeros(2), log_p, 10_000; algorithm=:am)
using MCMCChains, StatsPlots # MCMCChains & StatsPlots がインストールされていると仮定...
c = Chains(o.X[1]', start=o.params.b, thin=o.params.thin); plot(c)
```

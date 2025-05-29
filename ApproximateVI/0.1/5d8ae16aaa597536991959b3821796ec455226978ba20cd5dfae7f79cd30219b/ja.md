# 基本的な使い方:

```
q, logev = VI(logp, μ, σ²=0.1; S = 100, iterations = 1, show_every = -1)
```

近似ガウス後方分布と対数証拠を返します。

# 引数

最も基本的な引数の説明が続きます。

  * `logp` は（正規化されていない）対数後方分布、すなわち結合対数尤度を表す関数です。
  * `μ` は近似ガウス後方分布の初期平均です。
  * `σ²` は近似ガウス後方分布の初期共分散を σ² * I として指定します。デフォルト値は `0.1` です。
  * `S` は下限積分を近似するために引かれるサンプルの数です。
  * `iterations` は下限（elbo）に対する最適化を何回実行するかを指定します。
  * `show_every`: `show_every` 回のイテレーションごとに進捗を報告します。

# 出力

  * `q` は `Distributions.MvNormal` 型として返される近似後方分布です。
  * `logev` は近似対数証拠です。

# 例

```julia-repl
# ベイズ線形回帰の後方分布を推定し、正確な結果と比較する
julia> using LinearAlgebra, Distributions
julia> D = 4; X = randn(D, 1000); W = randn(D); β = 0.3; α = 1.0;
julia> Y = vec(W'*X); Y += randn(size(Y))/sqrt(β);
julia> Sn = inv(α*I + β*(X*X')) ; mn = β*Sn*X*Y; # 正確な後方分布
julia> posterior, logev = VI( w -> logpdf(MvNormal(vec(w'*X), sqrt(1/β)), Y) + logpdf(MvNormal(zeros(D),sqrt(1/α)), w), randn(D); S = 1_000, iterations = 15);
julia> display([mean(posterior) mn])
julia> display([cov(posterior)  Sn])
julia> display(logev) # 負の対数証拠を表示
```

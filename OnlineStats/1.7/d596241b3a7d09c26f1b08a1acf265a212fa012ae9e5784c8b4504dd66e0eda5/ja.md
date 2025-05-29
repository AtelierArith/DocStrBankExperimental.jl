```
StatLearn(args...; penalty=zero, rate=LearningRate())
```

パラメータに対して線形なモデルを（確率的近似を通じて）フィットします。StatLearnが近似的に最小化する（オフライン）目的関数は次の通りです。

$$
(1/n) ∑ᵢ f(yᵢ, xᵢ'β) + ∑ⱼ λⱼ g(βⱼ),
$$

ここで、$fᵢ$は応答変数と線形予測子の損失関数、$λⱼ$sは非負の正則化パラメータ、$g$はペナルティ関数です。

確率的近似アルゴリズムは本質的にノイズがあるため、`StatLearn`の使用には注意が必要です。

# 引数

  * `loss = OnlineStats.l2regloss`: （近似的に）最小化される損失関数。

      * 回帰損失:

          * `l2regloss`: 二乗誤差損失
          * `l1regloss`: 絶対誤差損失
      * 分類（y ∈ {-1, 1}）損失:

          * `logisticloss`: ロジスティック回帰
          * `l1hingeloss`: サポートベクターマシンで使用される損失関数。
          * `DWDLoss(q)`: 一般化距離加重識別（平滑化された`l1hingeloss`）
  * `algorithm = MSPI()`: 使用される確率的近似法。

      * 確率的勾配に基づくアルゴリズム:

          * `SGD()`: 確率的勾配降下法
          * `ADAGRAD()`: AdaGrad（SGDの適応版）
          * `RMSPROP()`: RMSProp（SGDの適応版）
      * 大域化最小化原理に基づくアルゴリズム:

          * `MSPI()`: 大域化確率的近接反復
          * `OMAS()`: 平均サロゲートによるオンラインMM
          * `OMAP()`: 平均パラメータによるオンラインMM
  * `λ = 0.0`: ペナルティ関数に使用されるハイパーパラメータ

      * ユーザーは要素ごとのペナルティハイパーパラメータ（`Vector{Float64}`）または単一のハイパーパラメータ（`Float64`）を提供できます。

## キーワード引数

  * `penalty`: 使用される正則化関数。

      * `zero`: ペナルティなし（デフォルト）
      * `abs`: （LASSO）絶対値によってペナルティが課されるパラメータ
      * `abs2`: （リッジ）二乗値によってペナルティが課されるパラメータ
      * `ElasticNet(α)`: α * （absペナルティ） + (1-α) * （abs2ペナルティ）
  * `rate = LearningRate(.6)`

# 例

```
x = randn(1000, 5)
y = x * range(-1, stop=1, length=5) + randn(1000)

o = fit!(StatLearn(MSPI()), zip(eachrow(x), y))
coef(o)

o = fit!(StatLearn(OnlineStats.l1regloss, ADAGRAD()), zip(eachrow(x), y))
coef(o)
```

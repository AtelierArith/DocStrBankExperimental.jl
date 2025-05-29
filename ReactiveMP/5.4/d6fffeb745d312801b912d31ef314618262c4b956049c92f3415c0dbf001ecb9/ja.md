```
CVIProjection(; parameters...)
```

共役変分推論 (CVI) 投影法のパラメータを表す構造体です。この構造体は `AbstractApproximationMethod` のサブタイプであり、CVI の設定を構成するために使用されます。

CVI は、共役形式の分布のファミリーに対して事後分布を投影することによって近似します。

# 要件

`CVIProjection` メソッドは、`ExponentialFamilyProjection` パッケージがインストールされ、現在の環境で `using ExponentialFamilyProjection` によってロードされていることを要求します。

# パラメータ

  * `rng::R`: サンプリングに使用される乱数生成器。デフォルトは `Random.MersenneTwister(42)` です。
  * `outsamples::S`: 出力メッセージ分布を近似するために使用されるサンプルの数。デフォルトは `100` です。
  * `out_prjparams::OF`: 出力メッセージのターゲット分布ファミリーを指定するために使用される形式パラメータ。`nothing`（デフォルト）の場合、形式は周辺形式から推測されます。
  * `in_prjparams::IFS`: 各入力エッジのターゲット分布ファミリーを指定する NamedTuple のようなオブジェクト。キーは `:in_k` の形式で、`k` は入力エッジのインデックスです。`nothing`（デフォルト）の場合、形式は受信メッセージから推測されます。
  * `proposal_distribution::PD`: サンプルを生成するために使用される提案分布。提供されない場合や `nothing` に設定されている場合、受信メッセージから推測され、反復中に自動的に更新されます。
  * `sampling_strategy::SS`: logpdf を近似するための戦略：

      * `FullSampling(n)`: 分布から引き出された `n` サンプルを使用します（デフォルト: `n=10`）。計算時間が増加する代わりに、より正確な近似を提供します。
      * `MeanBased()`: 各分布の平均のみを単一のサンプルとして使用します。非線形ノードや複雑な分布に対しては、かなり速いですが、精度は低下します。

# 例

```julia
# デフォルト設定での標準CVI投影
method = CVIProjection()

# 平均ベースのサンプリングを使用した高速近似
method = CVIProjection(sampling_strategy = MeanBased())

# サンプル数を増やしたカスタム提案
using Distributions
proposal = FactorizedJoint((NormalMeanVariance(0.0, 1.0), NormalMeanVariance(0.0, 1.0)))
method = CVIProjection(
    proposal_distribution = ProposalDistributionContainer(proposal),
    sampling_strategy = FullSampling(1000)
)

# 出力メッセージのための投影ファミリーを指定
method = CVIProjection(out_prjparams = ProjectedTo(NormalMeanPrecision))

# 入力エッジのための投影ファミリーを指定
method = CVIProjection(in_prjparams = (in_1 = ProjectedTo(NormalMeanVariance), in_2 = ProjectedTo(GammaShapeRate)))
```

!!! note
    `CVIProjection` メソッドは、廃止された `CVI` の強化版であり、より良い安定性と改善された精度を提供します。パラメータとデフォルトは、実装の進化に伴い変更される可能性があります。


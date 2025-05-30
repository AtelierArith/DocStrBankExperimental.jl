```
RobustAdaptiveMetropolis
```

ロバスト適応メトロポリス-ヘイスティングス (RAM)。

これは、[ ^VIH12 ] で説明されているRAMアルゴリズムのシンプルな実装です。

# フィールド

  * `α`: 目標受け入れ率。デフォルト: 0.234。
  * `γ`: 適応減衰率の負の指数。デフォルト: `0.6`。
  * `S`: 共分散行列の初期下三角のコレスキー因子。指定されている場合は、`LowerTriangular`に変換可能である必要があります。デフォルト: `nothing`、これは単位行列として解釈されます。
  * `eigenvalue_lower_bound`: 適応コレスキー因子の固有値の下限。デフォルト: `0.0`。
  * `eigenvalue_upper_bound`: 適応コレスキー因子の固有値の上限。デフォルト: `Inf`。

# 例

以下は、シンプルなガウスモデルを実装し、RAMアルゴリズムを使用してサンプリングする方法を示しています。

```jldoctest ram-gaussian; setup=:(using Random; Random.seed!(1234);)
julia> using AdvancedMH, Distributions, MCMCChains, LogDensityProblems, LinearAlgebra

julia> # 平均0でいくつかの共分散を持つガウスを定義します。
       struct Gaussian{A}
           Σ::A
       end

julia> # LogDensityProblemsインターフェースを実装します。
       LogDensityProblems.dimension(model::Gaussian) = size(model.Σ, 1)

julia> function LogDensityProblems.logdensity(model::Gaussian, x)
           d = LogDensityProblems.dimension(model)
           return logpdf(MvNormal(zeros(d),model.Σ), x)
       end

julia> LogDensityProblems.capabilities(::Gaussian) = LogDensityProblems.LogDensityOrder{0}()

julia> # モデルを構築します。相関を0.5に設定します。
       model = Gaussian([1.0 0.5; 0.5 1.0]);

julia> # 結果のチェーンで取得したいサンプル数。
       num_samples = 10_000;

julia> # ウォームアップステップの数、すなわち提案の共分散を適応させるためのステップ数。
       # これらは結果のチェーンには含まれません。デフォルトでは、`sample`呼び出しで`discard_initial=num_warmup`です。
       # これらを含めるには、`discard_initial=0`を`sample`に渡します。
       num_warmup = 10_000;

julia> # サンプリング！
       chain = sample(
            model,
            RobustAdaptiveMetropolis(),
            num_samples;
            chain_type=Chains, num_warmup, progress=false, initial_params=zeros(2)
        );

julia> isapprox(cov(Array(chain)), model.Σ; rtol = 0.2)
true
```

固有値を制限して、あまりにも小さすぎるまたは大きすぎる値を避けることも可能です。 [ ^VIH12 ] の13ページを参照してください。

```jldoctest ram-gaussian
julia> chain = sample(
           model,
           RobustAdaptiveMetropolis(eigenvalue_lower_bound=0.1, eigenvalue_upper_bound=2.0),
           num_samples;
           chain_type=Chains, num_warmup, progress=false, initial_params=zeros(2)
       );

julia> norm(cov(Array(chain)) - [1.0 0.5; 0.5 1.0]) < 0.2
true
```

# 参考文献

[^VIH12]: Vihola (2012) ロバスト適応メトロポリスアルゴリズムと強制された受け入れ率、統計と計算。

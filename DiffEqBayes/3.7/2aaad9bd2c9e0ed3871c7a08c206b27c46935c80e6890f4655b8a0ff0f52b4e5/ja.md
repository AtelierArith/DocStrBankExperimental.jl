```julia
dynamichmc_inference(
    problem,
    algorithm,
    t,
    data,
    parameter_priors;
    ...
)
dynamichmc_inference(
    problem,
    algorithm,
    t,
    data,
    parameter_priors,
    parameter_transformations;
    σ_priors,
    sample_u0,
    rng,
    num_samples,
    AD_gradient_kind,
    save_idxs,
    solve_kwargs,
    mcmc_kwargs
)

```

ODE問題のためのMCMCを実行します。`DynamicHMC.mcmc_with_warmup`によって返されるものに似た`NamedTuple`を返し、`ℝⁿ`から変換された後部の値のベクトルを含む`posterior`フィールドが追加されます。

# 引数

  * `problem`はODE問題です
  * `algorithm`はODEアルゴリズムです
  * `t`は解が`data`と比較される時間値です
  * `data`はデータの行列で、`t`の各要素に対して1列があります
  * `parameter_priors`はパラメータの数と同じ長さの反復可能なもので、それに対する事前分布として使用され、比較可能な構造を持つ必要があります。
  * `parameter_transformations`: `ℝⁿ`を有効なパラメータのベクトルにマッピングするための`TransformVariables`変換です。

# キーワード引数

  * `rng`はMCMCに使用される乱数生成器です。デフォルトはグローバルなものです。
  * `num_samples`はMCMCのサンプル数です（デフォルト: 1000）
  * `AD_gradient_kind`は`LogDensityProblems.ADgradient`に渡され、対応するライブラリを`import`する必要があります。
  * `solve_kwargs`は`solve`に渡されます
  * `mcmc_kwargs`は`DynamicHMC.mcmc_with_warmup`にキーワード引数として渡されます

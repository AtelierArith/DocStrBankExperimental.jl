```julia
mcmc_with_warmup(
    rng,
    ℓ,
    N;
    initialization,
    warmup_stages,
    algorithm,
    reporter
)

```

NUTSを使用してMCMCを実行し、返されないウォームアップを含みます。次の`NamedTuple`を返します。

  * `posterior_matrix`：位置ベクトルの行列、`[parameter_index, draw_index]`でインデックス付けされます。
  * `tree_statistics`：各サンプルのツリー統計のベクトル。
  * `κ`および`ϵ`：適応されたメトリックとステップサイズ。

# 引数

  * `rng`：乱数生成器、例：`Random.default_rng()`。
  * `ℓ`：`LogDensityProblems`パッケージのAPIをサポートする対数密度。
  * `N`：ウォームアップ後の推論のためのサンプル数。

# キーワード引数

  * `initialization`：以下を参照。
  * `warmup_stages`：ウォームアップステージのシーケンス。[`default_warmup_stages`](@ref)および[`fixed_stepsize_warmup_stages`](@ref)を参照；後者は初期化に`ϵ`を必要とします。
  * `algorithm`：[`NUTS`](@ref)を参照。最大深度を除いて、これを変更する必要は非常に低いです。
  * `reporter`：進捗が報告される方法。デフォルトでは、ログメッセージメカニズムを使用して対話型セッションのために詳細に報告され（[`LogProgressReport`](@ref)を参照）、非対話型セッションでは報告されません（[`NoProgressReport`](@ref)を参照）。

# 初期化

`initialization`キーワード引数は、以下のフィールドを含むことができる`NamedTuple`である必要があります（すべてオプションであり、合理的なデフォルトが提供されます）：

  * `q`：初期位置。*デフォルト*：各座標のためのランダム（均一[-2,2]）。
  * `κ`：運動エネルギーの仕様。*デフォルト*：単位行列のガウス分布。
  * `ϵ`：初期ステップサイズのスカラー、またはヒューリスティックファインダーのための`nothing`。

# 使用例

固定ステップサイズを使用：

```julia
mcmc_with_warmup(rng, ℓ, N;
                 initialization = (ϵ = 0.1, ),
                 warmup_stages = fixed_stepsize_warmup_stages())
```

与えられた位置`q₀`から開始し、運動エネルギーをスケールダウン（まだ適応されます）：

```julia
mcmc_with_warmup(rng, ℓ, N;
                 initialization = (q = q₀, κ = GaussianKineticEnergy(5, 0.1)))
```

密なメトリックを使用：

```julia
mcmc_with_warmup(rng, ℓ, N;
                 warmup_stages = default_warmup_stages(; M = Symmetric))
```

初期ステップサイズ検索を無効にする（明示的に提供され、まだ適応されます）：

```julia
mcmc_with_warmup(rng, ℓ, N;
                 initialization = (ϵ = 1.0, ),
                 warmup_stages = default_warmup_stages(; stepsize_search = nothing))
```

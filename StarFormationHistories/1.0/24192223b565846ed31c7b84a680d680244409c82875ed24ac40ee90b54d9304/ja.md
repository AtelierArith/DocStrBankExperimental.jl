```
result = fit_templates(models::AbstractVector{T},
                       data::AbstractMatrix{<:Number};
                       x0::AbstractVector{<:Number} = ones(S,length(models)),
                       kws...) where {S <: Number, T <: AbstractMatrix{S}}
```

最大尤度推定（MLE）と事後最大推定（MAP）を見つけるための係数 `coeffs` を求めます。合成ヘッセ図モデルは `sum(models .* coeffs)` であり、提供されたテンプレート `models` と観測されたヘッセ図 `data` を使用します。モデルが与えられたときのデータの尤度に対してポアソン尤度比（[Dolphin 2002](https://ui.adsabs.harvard.edu/abs/2002MNRAS.332...91D) の式7–10）を利用します。このメソッドの結果と、ハミルトンモンテカルロを介して事後分布をサンプリングする [`hmc_sample`](@ref) の比較については、ドキュメントの例を参照してください。

# 引数

  * `models::AbstractVector{AbstractMatrix{<:Number}}`: 考慮される単純星団（SSP）のためのテンプレートヘッセ図のリスト。すべて同じサイズでなければなりません。
  * `data::AbstractMatrix{<:Number}`: 観測されたヘッセ図。`models` に含まれるテンプレートのサイズと一致する必要があります。

# キーワード引数

  * `x0`: 星質量係数の初期推定値のベクトル。基本的にこのキーワード引数を計算して渡す必要があります。恒常的な星形成率を仮定して `x0` を準備するために [`StarFormationHistories.construct_x0`](@ref) を提供しています。これは通常良い初期推定です。

他の `kws...` は `Optim.options` に渡され、最適化の収束基準などを設定します。

# 戻り値

`result` は二つの [`StarFormationHistories.LogTransformFTResult`](@ref) を含む `NamedTuple` です。`result` の二つのコンポーネントは `result.map` または `result[1]` で、MAP最適化の結果を含み、`result.mle` または `result[2]` で、MLE最適化の結果を含みます。 [`StarFormationHistories.LogTransformFTResult`](@ref) のドキュメントにはこれらの型に関する詳細情報が含まれていますが、簡単に言うと、以下のフィールドを含み、例えば `result.map.μ`、`result.map.σ` などでアクセスできます：

  * `μ::Vector{<:Number}` は最大値での最適化された `coeffs` です。
  * `σ::Vector{<:Number}` は `μ` で評価された逆ヘッセ行列の推定から計算された係数 `μ` の標準誤差です。尤度（または事後）の最大値でのヘッセ行列の逆は、パラメータの分散共分散行列の推定量ですが、最適化される関数が最大値の周りでほぼ二次的である場合（すなわち、最適化される関数が最大値の周りでほぼ二次的である場合）にのみ正確です。MAP推定に対してはこれがしばしば当てはまりますが、MLEでの係数が ≈0 の場合に見つかる誤差は通常非現実的に小さいです。0よりもかなり大きい係数に対しては、MAPとMLEからの `σ` 値は通常5〜10％の範囲で一致します。
  * `invH::Matrix{<:Number}` は `σ` を導出するために使用された `μ` での逆ヘッセ行列の推定です。最適化は対数変換の下で行われ、`θ[j] = log(coeffs[j])` が実際に最適化されるパラメータです。したがって、ヘッセ行列のエントリは実際には

$$
H^{(j,k)} ( \boldsymbol{\hat \theta} ) = \left. \frac{\partial^2 \, J(\boldsymbol{\theta})}{\partial \theta_j \, \partial \theta_k} \right\vert_{\boldsymbol{\theta}=\boldsymbol{\hat \theta}}
$$

  * `result` は `Optim.jl` からの最適化によって返される完全なオブジェクトで、`Optim.MultivariateOptimizationResults` 型です。この生の出力を扱うときは、最適化が `θ[j] = log(coeffs[j])` で行われることを忘れないでください。たとえば、`result.map.μ` を `exp.(Optim.minimizer(result.map.result))` として計算します。

[`StarFormationHistories.LogTransformFTResult`](@ref) 型の特別な特性は、上記で議論した逆ヘッセ近似を使用して、結果から `N::Integer` のランダムパラメータサンプルを描画できることです。これを行うには `rand(result.map, N)` を実行します。この型は `Distributions.jl` のランダムサンプリングAPIを実装しているため、他の標準的なサンプリング方法も機能するはずです。私たちのテストでは、これらのサンプルはハミルトンモンテカルロを介して事後分布をサンプリングする [`hmc_sample`](@ref) からのサンプルと非常に良好に比較されます。これにより、より堅牢ですがはるかに高価です。これらのメソッドの比較は例で示しています。

# 注意事項

  * このメソッドは、パラメータの不確実性を推定するために使用できる逆ヘッセ行列近似を構築および追跡するため、内部的に `Optim.jl` の `BFGS` メソッドを使用します。BFGS は、パラメータの数が多い（同等に多くの `models` がある）場合、LBFGS（[`StarFormationHistories.fit_templates_lbfgsb`](@ref) に使用される）よりもはるかにメモリを消費します。そのため、数百を超える大規模なモデルグリッドを使用している場合は、MLEを解くためにLBFGSを検討し、事後分布をサンプリングするために [`hmc_sample`](@ref) を使用することをお勧めします。
  * 私たちが `Optim.jl` から使用するBFGSの実装は、反復中にBLAS操作を使用します。Juliaに付属するOpenBLASは、Julia自体が単一スレッドで起動されていても、しばしば複数のスレッドで実行されることがデフォルトです。現在のBLASスレッド数は `import LinearAlgebra: BLAS; BLAS.get_num_threads()` で確認できます。この関数の典型的な問題サイズでは、BLASスレッド数が多いとパフォーマンスが低下することが実際に見られます。このため、BLASを単一スレッドモードで使用することをお勧めします。これを設定するには `import LinearAlgebra: BLAS; BLAS.set_num_threads(1)` とします。

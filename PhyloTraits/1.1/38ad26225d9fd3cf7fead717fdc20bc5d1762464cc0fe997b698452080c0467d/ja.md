```
PhyloNetworkLinearModel <: GLM.LinPredModel
```

系統的線形モデルの表現。

## フィールド

`lm`, `V`, `Vy`, `RL`, `Y`, `X`, `logdetVy`, `reml`, `ind`, `nonmissing`, `evomodel`, `model_within` および `formula`。特定のフィールドに関する詳細情報を取得するには、次の構文パターンを使用できます。たとえば、`lm` フィールドについて知りたい場合は、`?PhyloNetworkLinearModel.lm` を実行します。

## 適用されるメソッド

次の StatsAPI / StatsBase 関数を適用できます: `coef`, `nobs`, `vcov`, `stderror`, `confint`, `coeftable`, `dof_residual`, `dof`, `deviance`, `residuals`, `response`, `predict`, `loglikelihood`, `nulldeviance`, `nullloglikelihood`, `r2`, `adjr2`, `aic`, `aicc`, `bic`, `ftest`, `lrtest` など。

種レベルの特性モデルの推定分散率と推定平均（[`ContinuousTraitEM`](@ref) を参照）を取得するには、それぞれ [`sigma2_phylo`](@ref) と [`mu_phylo`](@ref) を使用できます。

関連する場合、推定された個体レベル/種内分散は [`sigma2_within`](@ref) を使用して取得できます。

Pagel の λ モデルの最適化された λ パラメータ（[`PagelLambda`](@ref) を参照）は、[`lambda_estim`](@ref) を使用して取得できます。

祖先状態の再構築は [`ancestralreconstruction`](@ref) を使用して実行できます。

## 種内変動

応答特性/変数の真の種/集団平均（または残差: 予測子に条件付けられた）は、𝒩(·, σ²ₛV) として共同モデル化され、ここで V は特性モデル（[`ContinuousTraitEM`](@ref) を参照）および種ネットワークに依存します。σ²ₛ は種間分散率です。

種内変動は、個体レベルの応答が真の種平均の周りで iid 𝒩(0, σ²ₑ) であると仮定することによってモデル化され、したがって種レベルのサンプル平均（予測子に条件付けられた）は 𝒩(·, σ²ₛV + σ²ₑD⁻¹) として共同モデル化されます。ここで σ²ₑ は種内分散であり、D⁻¹ はエントリが逆サンプルサイズである対角行列です（[`WithinSpeciesCTM`](@ref) を参照）。

上記の2つのモデルは、種レベルのサンプル平均（または予測子に条件付けられた残差）のための共同分布の観点から表現できますが、種内変動を考慮したモデルを適合させるには、より多くのデータが必要です。つまり、サンプル平均が真の集団平均の推定値であることを認識するモデルです。種内変動なしでモデルを適合させるには、種平均に関するデータが十分です。種内変動を含むモデルを適合させるには、各種の応答変数の種平均と標準偏差が必要です。

`phylolm` は、種レベルの統計（「平均応答」と「応答の標準偏差」）または個体レベルのデータから、種内変動を持つモデルを適合させることができます（この場合、種レベルの統計は内部で計算されます）。これらの2つの入力選択肢に関する詳細は、[`phylolm`](@ref) を参照してください。

オブジェクト内で、`obj.Y` と `obj.X` は観測された種平均です。`predict`, `residuals` および `response` は種レベルでの値を返します。

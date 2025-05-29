loco_scan(y::Matrix{Float64}, dfG::DataFrame; kwargs...)

LOCOデータ構造のための共変量なしの単一形質スキャン。

# 引数

  * `y`は表現型列の行列です。
  * `dfG`は染色体、遺伝子座などの遺伝型値と遺伝型情報を含むデータフレームです。
  * `kwargs`は`BulkLMM.scan()`関数に関連するオプションのキーワード引数です。例えば：

```
`reml` = false, `permutation_test` = true, `nperms` = 1000, 
`weights` = missing, `prior_variance` = 0.0, `prior_sample_size` = 0.0。詳細については
`BulkLMM`のドキュメントを参照してください。
```

# 例

```julia
loco_scan(y, df_geno;
		 reml = false, permutation_test = true, nperms = 1000, 
		 weights = missing, prior_variance = 0.0, prior_sample_size = 0.0)
```

___

loco_scan(y::Matrix{Float64}, G::Vector{Matrix{Float64}}, K::Vector{Matrix{Float64}}; 	kwargs...)

LOCOデータ構造のための共変量なしの単一形質スキャン。

# 引数

  * `y`は表現型列の行列です。
  * `G`は染色体に基づく遺伝型行列のベクトルです。
  * `K`は親族行列のベクトルです。
  * `kwargs`は`BulkLMM.scan()`関数に関連するオプションのキーワード引数です。例えば：

```
`reml` = false, `permutation_test` = true, `nperms` = 1000, 
`weights` = missing, `prior_variance` = 0.0, `prior_sample_size` = 0.0。詳細については
`BulkLMM`のドキュメントを参照してください。
```

```julia
loco_scan(y, arr_geno, arr_kinship;
		 reml = false, permutation_test = true, nperms = 1000, 
		 weights = missing, prior_variance = 0.0, prior_sample_size = 0.0)
```

___

loco_scan(y::Matrix{Float64}, G::Vector{Matrix{Float64}}, covar::Matrix{Float64},         K::Vector{Matrix{Float64}};	kwargs...)

LOCOデータ構造のための共変量ありの単一形質スキャン。

# 引数

  * `y`は表現型列の行列です。
  * `G`は染色体に基づく遺伝型行列のベクトルです。
  * `covar`は共変量列の行列です。
  * `K`は親族行列のベクトルです。
  * `kwargs`は`BulkLMM.scan()`関数に関連するオプションのキーワード引数です。例えば：

```
`reml` = false, `permutation_test` = true, `nperms` = 1000, 
`weights` = missing, `prior_variance` = 0.0, `prior_sample_size` = 0.0。詳細については
`BulkLMM`のドキュメントを参照してください。
```

# 例

```julia
loco_scan(y, arr_geno, covar, arr_kinship;
		 reml = false, permutation_test = true, nperms = 1000, 
		 weights = missing, prior_variance = 0.0, prior_sample_size = 0.0)
```

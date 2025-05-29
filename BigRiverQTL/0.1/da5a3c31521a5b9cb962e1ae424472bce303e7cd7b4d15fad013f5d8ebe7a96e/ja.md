loco_bulkscan(y::Matrix{Float64}, dfG::DataFrame; kwargs...)

LOCOデータ構造のための共変量なしの単一形質スキャン。

# 引数

  * `y`は表現型列の行列です。
  * `dfG`は染色体、遺伝子座などの遺伝型値と遺伝型情報を含むデータフレームです。
  * `kwargs`は`BulkLMM.bulkscan()`関数に関連するオプションのキーワード引数です。例えば：

```
- method::String = "null-grid", h2_grid::Array{Float64, 1} = collect(0.0:0.1:0.9),
- nb::Int64 = Threads.nthreads(), 
- nt_blas::Int64 = 1, 
- weights::Union{Missing, Array{Float64, 1}} = missing,
- prior_variance::Float64 = 1.0, prior_sample_size::Float64 = 0.0,
- reml::Bool = false, optim_interval::Int64 = 1,
- output_pvals::Bool = false, chisq_df::Int64 = 1
```

詳細については`BulkLMM`のドキュメントを参照してください。

# 例

```julia
loco_bulkscan(y, df_geno;
		 method = "null-grid", h2_grid = collect(0.0:0.1:0.9),
		 reml = false, weights = missing, prior_variance = 0.0, prior_sample_size = 0.0)
```

___

loco_bulkscan(y::Matrix{Float64}, G::Vector{Matrix{Float64}}, K::Vector{Matrix{Float64}}; 	kwargs...)

LOCOデータ構造のための共変量なしの単一形質スキャン。

# 引数

  * `y`は表現型列の行列です。
  * `G`は染色体に基づく遺伝型行列のベクトルです。
  * `K`は親族行列のベクトルです。
  * `kwargs`は`BulkLMM.scan()`関数に関連するオプションのキーワード引数です。例えば：

```
- method::String = "null-grid", h2_grid::Array{Float64, 1} = collect(0.0:0.1:0.9),
- nb::Int64 = Threads.nthreads(), 
- nt_blas::Int64 = 1, 
- weights::Union{Missing, Array{Float64, 1}} = missing,
- prior_variance::Float64 = 1.0, prior_sample_size::Float64 = 0.0,
- reml::Bool = false, optim_interval::Int64 = 1,
- output_pvals::Bool = false, chisq_df::Int64 = 1
```

詳細については`BulkLMM`のドキュメントを参照してください。

```julia
loco_bulkscan(y, arr_geno, arr_kinship;
	method = "null-grid", h2_grid = collect(0.0:0.1:0.9),
	reml = false, weights = missing, prior_variance = 0.0, prior_sample_size = 0.0)
```

___

loco_bulkscan(y::Matrix{Float64}, G::Vector{Matrix{Float64}}, covar::Matrix{Float64},         K::Vector{Matrix{Float64}};	kwargs...)

LOCOデータ構造のための共変量ありの単一形質スキャン。

# 引数

  * `y`は表現型列の行列です。
  * `G`は染色体に基づく遺伝型行列のベクトルです。
  * `covar`は共変量列の行列です。
  * `K`は親族行列のベクトルです。
  * `kwargs`は`BulkLMM.scan()`関数に関連するオプションのキーワード引数です。例えば：

```
- method::String = "null-grid", h2_grid::Array{Float64, 1} = collect(0.0:0.1:0.9),
- nb::Int64 = Threads.nthreads(), 
- nt_blas::Int64 = 1, 
- weights::Union{Missing, Array{Float64, 1}} = missing,
- prior_variance::Float64 = 1.0, prior_sample_size::Float64 = 0.0,
- reml::Bool = false, optim_interval::Int64 = 1,
- output_pvals::Bool = false, chisq_df::Int64 = 1
```

詳細については`BulkLMM`のドキュメントを参照してください。

# 例

```julia
loco_scan(y, arr_geno, covar, arr_kinship;
	method = "null-grid", h2_grid = collect(0.0:0.1:0.9),
	reml = false, weights = missing, prior_variance = 0.0, prior_sample_size = 0.0)
```

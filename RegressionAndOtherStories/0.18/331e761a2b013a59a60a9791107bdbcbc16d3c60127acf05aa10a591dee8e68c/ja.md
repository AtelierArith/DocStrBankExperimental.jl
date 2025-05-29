チェーンのトレースと密度をプロットします。

```julia
plot_chains()

```

## 位置引数

```julia
* `df::DataFrame` # ドローを保持するDataFrame
* `pars::Vector{Symbol}` # 含めるシンボルまたは文字列のベクター
```

## キーワード引数

```julia
* `no_of_chains = 4` # チェーンの数
* 'no_of_draws = 1000' # 各チェーンのドロー数（ウォームアップ後）
```

KernelDensity.jlのキーワード引数は`kde()`に渡されます。

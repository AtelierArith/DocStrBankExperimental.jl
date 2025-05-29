生成された量の出力ファイルは、StanSample.jlによって作成されます。

```julia
stan_generate_quantities(m; ...)
stan_generate_quantities(m, id; ...)
stan_generate_quantities(m, id, chain; kwargs...)

```

### 必須引数

```julia
* `model`                    : SampleModel
```

### オプションの位置引数

```julia
* `id=1`                     : チェーンID、1:model.num_chainsの範囲内である必要があります
* `chain="1"`                : CSVファイルのサフィックス、例: ...chain_1_1.csv 
```

チェーンサフィックス `...chain_i_j` では：

```julia
i : 1:num_julia_chainsのインデックス 
j : 1:num_cpp_chainsのインデックス 
```

この関数は、`id` と `chain` の値をチェックします。正しければ、DataFrameが返されます。各呼び出しは新しい値のセットを返します。

詳細は `?available_chains` を参照してください。

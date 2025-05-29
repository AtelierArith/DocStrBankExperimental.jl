```
logtransform([T=Float64], counts::DataMatrix;
             var_filter = hasproperty(counts.var, "feature_type") ? "feature_type" => isequal("Gene Expression") : nothing,
             var_filter_cols = hasproperty(counts.var, "feature_type") ? "feature_type" : nothing,
             scale_factor=10_000,
             var=:copy,
             obs=:copy)
```

`counts`を次の式を用いてLog₂変換します：

```
  log₂(1 + cᵢⱼ*scale_factor/(∑ᵢcᵢⱼ))
```

オプションで、`T`を指定してスパース変換行列の`eltype`を制御できます。`T=Float32`を使用すると、結果にほとんど影響を与えずにメモリ使用量を減らすことができます。なぜなら、下流の分析は依然としてFloat64で行われるからです。

  * `var_filter` - パラメータ推定に使用する変数（特徴）を制御します。`counts.var`に`feature_type`列が存在する場合、デフォルトは`"feature_type" => isequal("Gene Expression")`です。フィルタリングを無効にするには`nothing`に設定できます。フィルタの指定方法については、[`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter)を参照してください。
  * `var_filter_cols` - 特徴が一意であることを保証するために使用される追加の列です。`counts.var`に存在する場合、デフォルトは`"feature_type"`です。複数の列を指定するには、タプル/ベクターを使用します。追加の列を含めないには`nothing`に設定できます。
  * `var` - `:copy`（ソースの`var`のコピーを作成）または`:keep`（ソースの`var`オブジェクトを共有）にできます。
  * `obs` - `:copy`（ソースの`obs`のコピーを作成）または`:keep`（ソースの`obs`オブジェクトを共有）にできます。

# 例

```julia
julia> transformed = logtransform(counts)
```

メモリ使用量を減らすためにeltype Float32を使用：

```julia
julia> transformed = logtransform(Float32, counts)
```

関連情報： [`sctransform`](@ref)

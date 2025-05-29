```
tf_idf_transform([T=Float64], counts::DataMatrix;
                 var_filter = hasproperty(counts.var, "feature_type") ? "feature_type" => isequal("Gene Expression") : nothing,
                 var_filter_cols = hasproperty(counts.var, "feature_type") ? "feature_type" : nothing,
                 scale_factor = 10_000,
                 idf = vec(size(counts,2) ./ max.(1,sum(counts.matrix; dims=2))),
                 annotate = true,
                 var = :copy,
                 obs = :copy)
```

`counts`のTF-IDF（用語頻度-逆文書頻度）変換を計算します。ここで、`tf`は`counts.matrix ./ max.(1, sum(counts.matrix; dims=1))`であり、式は`log( 1 + scale_factor * tf * idf )`です。

オプションで、`T`を指定してスパース変換行列の`eltype`を制御できます。`T=Float32`を使用すると、結果にほとんど影響を与えずにメモリ使用量を減らすことができます。なぜなら、下流の分析は依然としてFloat64で行われるからです。

  * `var_filter` - パラメータ推定に使用する変数（特徴）を制御します。`counts.var`に`feature_type`列が存在する場合、デフォルトは`"feature_type" => isequal("Gene Expression")`です。フィルタリングを無効にするには`nothing`に設定できます。フィルタの指定方法については、[`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter)を参照してください。
  * `var_filter_cols` - 特徴が一意であることを保証するために使用される追加の列です。`counts.var`に存在する場合、デフォルトは`"feature_type"`です。複数の列を指定するにはタプル/ベクターを使用します。追加の列を含めないには`nothing`に設定できます。
  * `annotate` - trueの場合、`idf`が`var`注釈として追加されます。
  * `var` - `:copy`（ソース`var`のコピーを作成）または`:keep`（ソース`var`オブジェクトを共有）にできます。
  * `obs` - `:copy`（ソース`obs`のコピーを作成）または`:keep`（ソース`obs`オブジェクトを共有）にできます。

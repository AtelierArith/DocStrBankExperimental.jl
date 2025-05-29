```
SCTransformModel([T=Float64], counts::DataMatrix;
                 var_filter = hasproperty(counts.var, :feature_type) ? :feature_type => isequal("Gene Expression") : nothing,
                 rtol=1e-3, atol=0.0, annotate=true,
                 post_var_filter=:, post_obs_filter=:,
                 obs=:copy,
                 kwargs...)
```

`counts`のための`SCTransform`パラメータ推定を計算し、同じデータセットまたは別のデータセットに適用できるSCTransformModelを作成します。デフォルトでは「Gene Expression」特徴のみを使用します。

オプションで、`T`を指定してスパース変換行列の`eltype`を制御できます。`T=Float32`を使用すると、結果にほとんど影響を与えずにメモリ使用量を減らすことができます。なぜなら、下流の分析は依然としてFloat64で行われるからです。

  * `var_filter` - パラメータ推定に使用する変数（特徴）を制御します。`counts.var`に`feature_type`列が存在する場合、デフォルトは`"feature_type" => isequal("Gene Expression")`です。フィルタリングを無効にするには`nothing`に設定できます。フィルタを指定する方法については、[`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter)を参照してください。
  * `var_filter_cols` - 特徴が一意であることを保証するために使用される追加の列です。`counts.var`に存在する場合、デフォルトは"feature_type"です。複数の列を指定するにはTuple/Vectorを使用します。追加の列を含めないには`nothing`に設定できます。
  * `rtol` - 低ランク近似を構築する際の相対許容誤差。
  * `atol` - 低ランク近似を構築する際の絶対許容誤差。
  * `annotate` - SCTransformパラメータ推定を特徴注釈として含めるにはtrueに設定します。
  * `post_var_filter` - sctransform後に変数（特徴）フィルタリングを適用するのと同等ですが、計算的により効率的です。
  * `post_obs_filter` - sctransform後に観察（細胞）フィルタリングを適用するのと同等ですが、計算的により効率的です。
  * `obs` - `:copy`（ソース`obs`のコピーを作成）または`:keep`（ソース`obs`オブジェクトを共有）にできます。
  * `kwargs...` - 追加の`kwargs`は[`SCTransform.scparams`](https://github.com/rasmushenningsson/SCTransform.jl)に渡されます。

# 例

`SCTransformModel`を設定する（Gene Expression特徴）:

```
julia> SCTransformModel(counts)
```

`SCTransformModel`を設定する（Antibody Capture特徴）:

```
julia> SCTransformModel(counts; var_filter = :feature_type => isequal("Antibody Capture"))
```

参照: [`sctransform`](@ref), [`SCTransform.scparams`](https://github.com/rasmushenningsson/SCTransform.jl), [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter)

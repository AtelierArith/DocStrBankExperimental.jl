```
select_features(selector,
                X::DataFrame,
                y::Vector;
                verbose::Bool=false)
```

重要度に基づいて特徴を選択します。重要度は `selector.method` によって定義され、`y` をターゲットとします。`verbose` が true の場合、ログが出力されます - これはデフォルトで false です。この関数は選択された特徴の名前のみを返します。

特徴 `X_data` が行列で、特徴名 `X_features` がベクトルの場合、`X` を `X_data` と `X_features`（この順序で）に置き換えることができます。

# 例

```jldoctest
julia> using RDatasets, FeatureSelectors, DataFrames

julia> boston = dataset("MASS", "Boston");

julia> selector = UnivariateFeatureSelector(method=pearson_correlation, k=5)
UnivariateFeatureSelector(FeatureSelectors.pearson_correlation, 5, nothing)

julia> select_features(
           selector,
           boston[:, Not(:MedV)],
           boston.MedV
       )
5-element Vector{String}:
 "LStat"
 "Rm"
 "PTRatio"
 "Indus"
 "Tax"

```

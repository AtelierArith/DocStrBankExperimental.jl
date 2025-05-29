```
impute!(data::A, imp; dims=:, kwargs...) -> A
```

配列 `data` の `missing` 値をインプテータ `imp` を使用して補完します。オプションで、補完する次元を指定できます。

# 引数

  * `data::AbstractArray{Union{T, Missing}}`: 次元 `dims` に沿って補完するデータ
  * `imp::Imputor`: 使用するインプテータメソッド

# キーワード引数

  * `dims=:`: 補完する次元。行列の場合は `:rows` と `:cols` もサポートされています。

# 戻り値

  * `AbstractArray{Union{T, Missing}}`: 補完された値を持つ入力 `data`

# 注意事項

1. 行列には `dims=2` の特別なケースが非推奨であり、`dims=:` は破壊的変更です。
2. すべての配列タイプに対して変更が保証されているわけではないため、結果を返します。
3. 内部で `eachslice` が使用されており、Julia 1.1 が必要です。

# 例

```jldoctest
julia> using Impute: Interpolate, impute!

julia> M = [1.0 2.0 missing missing 5.0; 1.1 2.2 3.3 missing 5.5]
2×5 Matrix{Union{Missing, Float64}}:
 1.0  2.0   missing  missing  5.0
 1.1  2.2  3.3       missing  5.5

julia> impute!(M, Interpolate(); dims=1)
2×5 Matrix{Union{Missing, Float64}}:
 1.0  2.0  3.0  4.0  5.0
 1.1  2.2  3.3  4.4  5.5

julia> M
2×5 Matrix{Union{Missing, Float64}}:
 1.0  2.0  3.0  4.0  5.0
 1.1  2.2  3.3  4.4  5.5
```

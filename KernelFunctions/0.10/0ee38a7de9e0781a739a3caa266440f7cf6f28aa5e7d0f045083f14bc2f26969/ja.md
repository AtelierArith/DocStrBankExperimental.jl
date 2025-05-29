```
prepare_heterotopic_multi_output_data(
    x::AbstractVector, y::AbstractVector{<:Real}, output_indices::AbstractVector{Int},
)
```

入力のコレクション `x`、観測値 `y`、および `output_indices` をマルチ出力カーネルで使用するのに適した形式に変換するユーティリティ機能です。各特徴で観測される出力が1つ（またはサブセット）のみである状況を処理します。すべての引数が互換性があることを確認し、入力のベクトルと出力のベクトルを返します。

`y[n]` は、特徴 `x[n]` における出力 `output_indices[n]` に関連付けられた観測値である必要があります。

```jldoctest
julia> x = [1.0, 2.0, 3.0];

julia> y = [-1.0, 0.0, 1.0];

julia> output_indices = [3, 2, 1];

julia> inputs, outputs = prepare_heterotopic_multi_output_data(x, y, output_indices);

julia> inputs
3-element Vector{Tuple{Float64, Int64}}:
 (1.0, 3)
 (2.0, 2)
 (3.0, 1)

julia> outputs
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```

他にも [`prepare_isotopic_multi_output_data`](@ref) を参照してください。

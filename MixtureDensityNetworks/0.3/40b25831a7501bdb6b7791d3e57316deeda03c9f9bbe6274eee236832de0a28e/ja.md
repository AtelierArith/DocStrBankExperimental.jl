```julia
generate_data(
    n_samples::Int64
) -> Tuple{Matrix{Float64}, Matrix{Float64}}

```

テスト目的のために合成データを生成します。

# パラメータ

  * `n_samples`: 生成したいサンプルの数。

# 戻り値

合成特徴 `X` とラベル `Y` をタプル `(X, Y)` として返します。

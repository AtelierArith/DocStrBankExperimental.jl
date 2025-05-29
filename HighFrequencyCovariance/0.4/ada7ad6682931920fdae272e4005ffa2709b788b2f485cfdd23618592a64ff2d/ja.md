```
regularise(
    mat::Hermitian,
    ts::SortedDataFrame,
    mat_labels::Vector,
    method::Symbol = :correlation_default;
    spacing::Union{Missing,<:Real} = missing,
    weighting_matrix = Diagonal(eltype(mat).(I(size(mat)[1]))),
    doDykstra = true,
    stop_at_first_correlation_matrix = true,
    max_iterates = 1000,
)
```

これは正則化技術の便利なラッパーです。

### 一般的な入力

  * `mat` - 正則化したい行列。
  * `ts` - ティックデータ。
  * `mat_labels` - 行列の各行/列の資産名。
  * `method`  - 使用したい方法。これは `:identity_regularisation`、`:eigenvalue_clean`、`:nearest_correlation_matrix` または `:nearest_psd_matrix` である可能性があります。また、`:covariance_default`（これは `:nearest_psd_matrix`）または `:correlation_default`（これは `:nearest_correlation_matrix`）を選択することもできます。

#### `:identity_regularisation` メソッドでのみ使用される入力。

  * `spacing` - アイデンティティ重みを選択する際に使用される間隔の間隔（`identity_regularisation` メソッドのみ）。

#### `:nearest_correlation_matrix` メソッドでのみ使用される入力。

  * `weighting_matrix` - 最も近いpsd行列を計算するために使用される重み行列（`:nearest_correlation_matrix` メソッドのみ）。
  * `doDykstra` - Dykstra補正を適用すべきか（`:nearest_correlation_matrix` メソッドのみ）。
  * `stop_at_first_correlation_matrix` - 最初の有効な相関行列で停止すべきか（`:nearest_correlation_matrix` メソッドのみ）。
  * `max_iterates` - 最大反復回数（`:nearest_correlation_matrix` メソッドのみ）。

### 戻り値

  * `Hermitian`

    regularise(      covariance*matrix::CovarianceMatrix,      ts::SortedDataFrame,      method::Symbol = :nearest*correlation*matrix;      apply*to*covariance::Bool = true,      spacing::Union{Missing,<:Real} = missing,      weighting*matrix = Diagonal(eltype(covariance*matrix.correlation).(I(size(covariance*matrix.correlation)[1]))),      doDykstra = true,      stop*at*first*correlation*matrix = true,      max_iterates = 1000,   )

これは正則化技術の便利なラッパーです。

### 一般的な入力

  * `covariance_matrix` - 正則化したい行列。
  * `ts` - ティックデータ。
  * `method`  - 使用したい方法。これは `:identity_regularisation`、`:eigenvalue_clean`、`:nearest_correlation_matrix` または `:nearest_psd_matrix` である可能性があります。また、`:covariance_default`（これは `:nearest_psd_matrix`）または `:correlation_default`（これは `:nearest_correlation_matrix`）を選択することもできます。
  * `apply_to_covariance` - 正則化を共分散行列に適用すべきか。falseの場合は相関行列に適用されます。

#### `:identity_regularisation` メソッドでのみ使用される入力。

  * `spacing` - アイデンティティ重みを選択する際に使用される間隔の間隔（`identity_regularisation` メソッドのみ）。

#### `:nearest_correlation_matrix` メソッドでのみ使用される入力。

  * `weighting_matrix` - 最も近いpsd行列を計算するために使用される重み行列（`:nearest_correlation_matrix` メソッドのみ）。
  * `doDykstra` - Dykstra補正を適用すべきか（`:nearest_correlation_matrix` メソッドのみ）。
  * `stop_at_first_correlation_matrix` - 最初の有効な相関行列で停止すべきか（`:nearest_correlation_matrix` メソッドのみ）。
  * `max_iterates` - 最大反復回数（`:nearest_correlation_matrix` メソッドのみ）。

### 戻り値

  * `CovarianceMatrix`

```

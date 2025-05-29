```
cov_to_cor_and_vol(
    mat::AbstractMatrix,
    duration_of_covariance_matrix::Dates.Period,
    duration_for_desired_vols::Dates.Period,
)

cov_to_cor_and_vol(
    mat::AbstractMatrix,
    duration_of_covariance_matrix::Real,
    duration_for_desired_vols::Real,
)
```

行列（共分散行列を表す）を `Hermitian` 相関行列とボラティリティのベクトルに変換します。

### 入力

  * `cor` - 相関行列。
  * `duration_of_covariance_matrix` - 共分散行列の期間。これらが実数として入力される場合、同じ単位でなければなりません。
  * `duration_for_desired_vols` - ボラティリティを求めるための期間。これらが実数として入力される場合、同じ単位でなければなりません。

### 戻り値

  * `Hermitian`。
  * ボラティリティの `Vector`。

    cov*to*cor*and*vol(       mat::AbstractMatrix,       duration*of*covariance*matrix*in*natural*units::Real,   )

### 入力

  * `cor` - 相関行列。
  * `duration_of_covariance_matrix_in_natural_units` - 共分散行列の期間。期間は、あなたが知っている単位で入力する必要があります（例えば、`SortedDataFrame` の `time_period_per_unit` など）。

### 戻り値

  * `Hermitian`。
  * ボラティリティの `Vector`。

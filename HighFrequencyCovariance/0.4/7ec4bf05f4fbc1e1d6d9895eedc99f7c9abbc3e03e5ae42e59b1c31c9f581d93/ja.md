```
nearest_correlation_matrix(
    mat::AbstractMatrix,
    weighting_matrix::Union{Diagonal,Hermitian} = Diagonal(Float64.(I(size(mat)[1])));
    doDykstra::Bool = true,
    stop_at_first_correlation_matrix::Bool = true,
    max_iterates::Integer = 1000,
)
```

行列を最も近い有効な相関行列（対角が1で、他のすべてのエントリが絶対値で1未満のpdf行列）にマッピングします。

### 入力

  * `mat` - 正則化したい行列。
  * `ts` - ティックデータ。
  * `weighting_matrix` - **最も近い**有効な相関行列を重み付けするために使用される重み行列。
  * `doDykstra` - Dykstra補正を行うべきか。
  * `stop_at_first_correlation_matrix` - すべての反復を行うまで繰り返すべきか、最初の有効な相関行列で停止すべきか。
  * `max_iterates` - 有効な相関行列に向けて行う最大反復回数。

### 戻り値

  * `Matrix`
  * 何回の反復が行われたかを示す整数
  * 収束メッセージを持つシンボル。

    nearest*correlation*matrix(       covariance*matrix::CovarianceMatrix,       ts::SortedDataFrame;       weighting*matrix::Union{Diagonal,Hermitian} = Diagonal(eltype(covariance*matrix.correlation).(I(size(covariance*matrix.correlation)[1]))),       doDykstra::Bool = true,       stop*at*first*correlation*matrix::Bool = true,       max_iterates::Integer = 1000,   )

行列を最も近い有効な相関行列（対角が1で、他のすべてのエントリが絶対値で1未満のpdf行列）にマッピングします。

### 入力

  * `covariance_matrix` - 正則化したい行列。
  * `ts` - ティックデータ。
  * `weighting_matrix` - **最も近い**有効な相関行列を重み付けするために使用される重み行列。
  * `doDykstra` - Dykstra補正を行うべきか。
  * `stop_at_first_correlation_matrix` - すべての反復を行うまで繰り返すべきか、最初の有効な相関行列で停止すべきか。
  * `max_iterates` - 有効な相関行列に向けて行う最大反復回数。

### 戻り値

  * `CovarianceMatrix`

    nearest*correlation*matrix(       covariance*matrix::CovarianceMatrix;       weighting*matrix::Union{Diagonal,Hermitian} = Diagonal(eltype(covariance*matrix.correlation).(I(size(covariance*matrix.correlation)[1]))),       doDykstra::Bool = true,       stop*at*first*correlation*matrix::Bool = true,       max_iterates::Integer = 1000,   )

行列を最も近い有効な相関行列（対角が1で、他のすべてのエントリが絶対値で1未満のpdf行列）にマッピングします。

### 入力

  * `covariance_matrix` - 正則化したい行列。
  * `weighting_matrix` - **最も近い**有効な相関行列を重み付けするために使用される重み行列。
  * `doDykstra` - Dykstra補正を行うべきか。
  * `stop_at_first_correlation_matrix` - すべての反復を行うまで繰り返すべきか、最初の有効な相関行列で停止すべきか。
  * `max_iterates` - 有効な相関行列に向けて行う最大反復回数。

### 戻り値

  * `CovarianceMatrix`

    nearest*correlation*matrix(       mat::Hermitian,       ts::SortedDataFrame;       weighting*matrix::Union{Diagonal,Hermitian} = Diagonal(eltype(mat).(I(size(mat)[1]))),       doDykstra::Bool = true,       stop*at*first*correlation*matrix::Bool = true,       max*iterates::Integer = 1000,   )

行列を最も近い有効な相関行列（対角が1で、他のすべてのエントリが絶対値で1未満のpdf行列）にマッピングします。

### 入力

  * `mat` - 正則化したい行列。
  * `weighting_matrix` - **最も近い**有効な相関行列を重み付けするために使用される重み行列。
  * `doDykstra` - Dykstra補正を行うべきか。
  * `stop_at_first_correlation_matrix` - すべての反復を行うまで繰り返すべきか、最初の有効な相関行列で停止すべきか。
  * `max_iterates` - 有効な相関行列に向けて行う最大反復回数。

### 戻り値

  * `Hermitian`

    nearest*correlation*matrix(      mat::Hermitian;      weighting*matrix::Union{Diagonal,Hermitian} = Diagonal(eltype(mat).(I(size(mat)[1]))),      doDykstra::Bool = true,      stop*at*first*correlation*matrix::Bool = true,      max*iterates::Integer = 1000,   )

行列を最も近い有効な相関行列（対角が1で、他のすべてのエントリが絶対値で1未満のpdf行列）にマッピングします。

### 入力

  * `covariance_matrix` - 正則化したい行列。
  * `ts` - ティックデータ。
  * `weighting_matrix` - **最も近い**有効な相関行列を重み付けするために使用される重み行列。
  * `doDykstra` - Dykstra補正を行うべきか。
  * `stop_at_first_correlation_matrix` - すべての反復を行うまで繰り返すべきか、最初の有効な相関行列で停止すべきか。
  * `max_iterates` - 有効な相関行列に向けて行う最大反復回数。

### 戻り値

  * `Hermitian`

### 参考文献

Higham NJ (2002). "Computing the nearest correlation matrix - a problem from finance." IMA Journal of Numerical Analysis, 22, 329–343. doi:10.1002/nla.258.

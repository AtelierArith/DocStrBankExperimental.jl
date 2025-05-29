```julia
spectral_truncation!(
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    ltrunc::Integer,
    mtrunc::Integer
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

次数 `ltrunc` および次数 `mtrunc` (両方とも0ベース) に対する三角トランケーション。次数 `l` がトランケーション `ltrunc` より大きいか、次数 `m` がトランケーション `mtrunc` より大きいすべての係数を設定することによって、スペクトル係数 `alms` をインプレースでトランケートします。

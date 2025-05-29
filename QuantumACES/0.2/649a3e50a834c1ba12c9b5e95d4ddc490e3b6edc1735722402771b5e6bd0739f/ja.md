```
nrmse_pdf(cov_eigenvalues::Vector{Float64}, nrmse_values::Vector{Float64}; epsilon::Real = 1e-5)
```

ゲート固有値推定器ベクトルの正規化RMS誤差（NRMSE）の確率密度関数（PDF）を返します。これは一般化カイ二乗分布に従い、その共分散行列は`cov_eigenvalues`の固有値を持ち、`nrmse_values`で指定された座標におけるものです。PDFの正規近似が最大値の`epsilon`の因子未満の場合、値は計算されません。

計算はJ. P. Imhof（1961）の「Computing the distribution of quadratic forms in normal variables」の式3.2に従います。

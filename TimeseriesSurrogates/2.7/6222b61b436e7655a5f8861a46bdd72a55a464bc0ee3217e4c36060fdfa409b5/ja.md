```
TFTDIAAFT(fϵ = 0.05; M::Int = 100, tol::Real = 1e-6, W::Int = 75)
```

[`TFTDIAAFT`](@ref)[^Lucio2012] は [`TFTDAAFT`](@ref) に似ていますが、サロゲートと元の時系列の周期グラムをよりよく一致させるための反復手順を追加します。これは、[`IAAFT`](@ref) が [`AAFT`](@ref) を改善する方法に類似しています。

`fϵ ∈ (0, 1]` は、保持される低周波数に対応するパワースペクトルの割合です。`M` は最大反復回数です。`tol` はパワースペクトル間の望ましい最大相対許容誤差です。`W` は、反復間で比較する際に周期グラムがビン分けされるビンの数です。

関連情報: [`TFTD`](@ref), [`TFTDAAFT`](@ref).

[^Lucio2012]: Lucio, J. H., Valdés, R., & Rodríguez, L. R. (2012). Improvements to surrogate data methods for nonstationary time series. Physical Review E, 85(5), 056202.

```
compute_δϵ_δψ(eop_iau2000a::EopIau2000A, JD::Number) -> (Float64, Float64)
```

IAU 2000A `eop_iau2000a` に基づいて、傾斜角 (`δΔϵ_2000`) と経度 (`δΔΨ_2000`) の天体極オフセット [arcsec] を計算します。

この関数は、GCRS に対する天体極オフセット (`δx` と `δy`) を変換することによってこれらの値を取得します。これらの値は、春分点に基づく IAU-2006 理論に必要です。

アルゴリズムは **[1]**(eq. 5.25) と **[2]**(`DPSIDEPS2000_DXDY2000`) から得られました。

# 参考文献

  * **[1]**: IERS (2010). 国際地球基準系と地心天体基準系との間の変換. IERS 技術ノート No. 36, 第5章.
  * **[2]**: ftp://hpiers.obspm.fr/eop-pc/models/uai2000.package

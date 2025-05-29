vaporpressure(specific*humidity::ClimGrid, sealevel*pressure::ClimGrid, orography::ClimGrid, daily_temperature::ClimGrid)

特定の湿度 (q)、海面気圧 (psl) (Pa)、地形 (orog) (m)、および日平均気温 (tas) (K) を用いて推定される水蒸気圧 (vp) (Pa) を返します。まず、海面気圧、地形、および日平均気温を使用して表面気圧の近似値が計算されます（[`approx_surfacepressure`](@ref）を参照）。次に、水蒸気圧は次のように計算されます：

$$
vp = \frac{q * sp}{q+0.622}
$$

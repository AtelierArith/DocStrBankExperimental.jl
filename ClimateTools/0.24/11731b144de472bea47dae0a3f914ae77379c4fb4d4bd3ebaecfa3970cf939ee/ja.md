approx*surfacepressure(sealevel*pressure::ClimGrid, orography::ClimGrid, daily_temperature::ClimGrid)

海面気圧 (*psl*) (Pa)、地形 (*orog*) (m)、および日平均気温 (*tas*) (K) を使用して、近似された表面気圧 (*sp*) (Pa) を返します。

$$
sp = psl * 10^{x}
$$

ここで、$x = \frac{-orog}{18400 * tas / 273.15}$

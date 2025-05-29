vaporpressure(surface*pressure::ClimGrid, specific*humidity::ClimGrid)

表面圧力（sp）（Pa）と比湿（q）に基づいて水蒸気圧（vp）（Pa）を返します。

$$
vp = \frac{q * sp}{q+0.622}
$$

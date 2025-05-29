meantemperature(temperatureminimum::ClimGrid, temperaturemaximum::ClimGrid)

最大気温と最小気温から計算された日平均気温を返します。日々の最大気温と最小気温は同じ単位でなければなりません。返される平均気温は、日々の最小気温および日々の最大気温と同じ単位です。

$$
Tmean = \frac{Tmax + Tmin}{2}
$$

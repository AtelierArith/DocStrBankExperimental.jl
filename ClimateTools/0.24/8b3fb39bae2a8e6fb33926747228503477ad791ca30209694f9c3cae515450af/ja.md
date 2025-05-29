diurnaltemperature(temperatureminimum::ClimGrid, temperaturemaximum::ClimGrid, α::Float64)

7:00 (午前7時) と 17:00 (午後5時) の間の温度の推定値を返します。この推定値は、日々の最低気温 (temperatureminimum) と日々の最高気温 (temperaturemaximum) の線形結合です。αの値は観測から別途推定する必要があり、場所によって異なります。日々の最高値と最低値は同じ単位で、摂氏またはケルビンでなければなりません。返される日中の温度は、日々の最低気温および日々の最高気温と同じ単位です。

$$
Tdiu = α * Tmin + (1 - α) * Tmax
$$

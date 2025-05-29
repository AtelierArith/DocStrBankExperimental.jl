```
function solar_azimuth_altitude(utc_time, lat, lon, alt)
```

与えられたUTC時間`utc_time`、緯度`lat`、経度`lon`、および高度`alt`に対して、その場所に対する太陽の方位角と太陽の高度角（度単位）を返します。

これは、Darin C. KoblickによるMatlabスクリプトのJulia（再）実装です [(link)](https://www.mathworks.com/matlabcentral/fileexchange/23051-vectorized-solar-azimuth-and-elevation-estimation)。

他の参考文献：

  * [http://stjarnhimlen.se/comp/tutorial.html#5](http://stjarnhimlen.se/comp/tutorial.html#5)
  * [http://www.stargazing.net/kepler/altaz.html](http://www.stargazing.net/kepler/altaz.html)

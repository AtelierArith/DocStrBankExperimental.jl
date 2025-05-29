```
et2utc(et, format, prec)
```

入力時間をJ2000からのエフェメリス秒でUTCのカレンダー、年の日、またはユリウス日形式に変換します。

### 引数

  * `et`: 入力エポック、J2000からのエフェメリス秒で指定
  * `format`: 出力エポックの形式。以下のいずれかである必要があります：

      * `:C`: カレンダー形式、UTC
      * `:D`: 年の日形式、UTC
      * `:J`: ユリウス日形式、UTC
      * `:ISOC`: ISOカレンダー形式、UTC
      * `:ISOD`: ISO年の日形式、UTC
  * `prec`: 小数秒または日数の精度の桁数

### 出力

指定された形式で入力エポックに相当する出力時間文字列を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/et2utc_c.html)

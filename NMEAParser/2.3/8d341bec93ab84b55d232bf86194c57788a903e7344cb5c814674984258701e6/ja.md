```
is_string_supported(nmea_string::AbstractString)
```

入力されたNMEA文字列のタイプがサポートされているかどうかを確認します。

# 引数

  * `nmea_string::AbstractString`: チェックされるNMEA文字列。

# 戻り値

  * `Bool`: NMEA文字列がサポートされている場合は`true`、そうでない場合は`false`。

# 例

```julia
julia> is_string_supported("$GPGGA,123519,4807.038,N,01131.000,E,1,08,0.9,545.4,M,46.9,M,,*47")
true
```

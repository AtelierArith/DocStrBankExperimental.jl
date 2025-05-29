```
compare_box_windspeed(city::String = "",
                      i_row::Int64 = 1;
                      lat::Float64 = 0.0,
                      long::Float64 = 0.0,
                      month::String = "Jan",
                      num_years::Int64 = 5)
```

指定された場所（都市または緯度/経度）における、特定の月の風速のボックスプロット分布を、指定された年数にわたって比較します。

# 引数

  * `city::String` : 有効な都市名、例："Oslo"、"Paris"、"Amsterdam"など。
  * `i_row::Int64` : 指定された場所に対して複数の一致がある場合、                  印刷されたDataFrameから行インデックスを提供することで                  希望のタイムゾーンを選択します。デフォルトは1に設定されています。

# 必須キーワード

  * `month::String` : 比較するデータの月、例："Jan"、"March"など。
  * `num_years::Int64` : データを比較する年数

# オプションキーワード

  * `lat::Float64` : 場所の地理的WGS84座標（°S < 0, °N > 0）
  * `long::Float64` : 場所の地理的WGS84座標（°W < 0, °E > 0）

# 例

```julia-repl
julia> compare_box_windspeed("Copenhagen", month = "Feb", num_years = 2)
[ Info: More than one match found, showing report for location in row 1.
[ Info: You can select another location by its row index.
2×4 DataFrame
 Row │ CITY        TIMEZONE           LATITUDE  LONGITUDE 
     │ String?     String31           Float64   Float64   
─────┼────────────────────────────────────────────────────
   1 │ Copenhagen  Europe/Copenhagen   55.6759    12.5655
   2 │ Copenhagen  America/New_York    43.8934   -75.6735
                 Copenhagen: Wind speed comparison for Feb over last 2 years          
         Timezone: Europe/Copenhagen                [Weather data by Open-Meteo.com]  
        ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓ 
        ┃╷             ┌────┬──────┐                 ╷                              ┃ 
   2021 ┃├─────────────┤    │      ├─────────────────┤                              ┃ 
        ┃╵             └────┴──────┘                 ╵                              ┃ 
        ┃╷                    ┌──────┬─────┐                      ╷                 ┃ 
   2022 ┃├────────────────────┤      │     ├──────────────────────┤                 ┃ 
        ┃╵                    └──────┴─────┘                      ╵                 ┃ 
        ┃ ╷           ┌───────┬────────┐                                          ╷ ┃ 
   2023 ┃ ├───────────┤       │        ├──────────────────────────────────────────┤ ┃ 
        ┃ ╵           └───────┴────────┘                                          ╵ ┃ 
        ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛ 
         0                                   30                                   60  
                                            [km/h]                                    
```

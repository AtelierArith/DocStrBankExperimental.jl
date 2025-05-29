```
map_correct_igrf(map_map::Matrix, map_alt,
                 map_xx::Vector, map_yy::Vector;
                 sub_igrf_date::Real = get_years(2013,293), # 20-Oct-2013
                 add_igrf_date::Real = -1,
                 zone_utm::Int       = 18,
                 is_north::Bool      = true,
                 map_units::Symbol   = :rad)
```

国際地磁気基準場（IGRF）を修正します。つまり、指定された日付のIGRFを引いたり加えたりして、地図のコアフィールドを修正します。

**引数:**

  * `map_map`:       `ny` x `nx` 2D グリッドマップデータ
  * `map_alt`:       `ny` x `nx` 2D グリッド高度マップデータ [m]
  * `map_xx`:        `nx` マップのx方向（経度）座標 [rad] または [deg] または [m]
  * `map_yy`:        `ny` マップのy方向（緯度）座標 [rad] または [deg] または [m]
  * `sub_igrf_date`: （オプション）引くIGRFコアフィールドの日付 [yr]、-1で無視
  * `add_igrf_date`: （オプション）加えるIGRFコアフィールドの日付 [yr]、-1で無視
  * `zone_utm`:      （オプション）UTMゾーン、`map_units = :utm` の場合のみ使用
  * `is_north`:      （オプション）trueの場合、地図は北半球にあり、`map_units = :utm` の場合のみ使用
  * `map_units`:     （オプション）マップのxx/yy単位 {`:rad`,`:deg`,`:utm`}

**戻り値:**

  * `map_map`: `ny` x `nx` 2D グリッドマップデータ、IGRF修正済み

```
map_correct_igrf(mapS::Union{MapS,MapSd,MapS3D};
                 sub_igrf_date::Real = get_years(2013,293), # 20-Oct-2013
                 add_igrf_date::Real = -1,
                 zone_utm::Int       = 18,
                 is_north::Bool      = true,
                 map_units::Symbol   = :rad)
```

国際地磁気基準場（IGRF）、すなわちコアフィールドを、指定された日付のIGRFを引いたり加えたりすることで地図を修正します。

**引数:**

  * `mapS`:          `MapS`、`MapSd`、または `MapS3D` スカラー磁気異常地図構造体
  * `sub_igrf_date`: （オプション）引くIGRFコアフィールドの日付 [年]、-1は無視
  * `add_igrf_date`: （オプション）加えるIGRFコアフィールドの日付 [年]、-1は無視
  * `zone_utm`:      （オプション）UTMゾーン、`map_units = :utm` の場合のみ使用
  * `is_north`:      （オプション）trueの場合、地図は北半球にあり、`map_units = :utm` の場合のみ使用
  * `map_units`:     （オプション）地図のxx/yy単位 {`:rad`,`:deg`,`:utm`}

**戻り値:**

  * `mapS`: `MapS`、`MapSd`、または `MapS3D` スカラー磁気異常地図構造体、IGRF修正済み

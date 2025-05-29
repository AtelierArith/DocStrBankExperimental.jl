```
map_correct_igrf!(mapS::Union{MapS,MapSd,MapS3D};
                  sub_igrf_date::Real = get_years(2013,293), # 20-Oct-2013
                  add_igrf_date::Real = -1,
                  zone_utm::Int       = 18,
                  is_north::Bool      = true,
                  map_units::Symbol   = :rad)
```

Correct the International Geomagnetic Reference Field (IGRF), i.e., core field, of a map by subtracting and/or adding the IGRF on specified date(s).

**Arguments:**

  * `mapS`:          `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct
  * `sub_igrf_date`: (optional) date of IGRF core field to subtract [yr], -1 to ignore
  * `add_igrf_date`: (optional) date of IGRF core field to add [yr], -1 to ignore
  * `zone_utm`:      (optional) UTM zone, only used if `map_units = :utm`
  * `is_north`:      (optional) if true, map is in northern hemisphere, only used if `map_units = :utm`
  * `map_units`:     (optional) map xx/yy units {`:rad`,`:deg`,`:utm`}

**Returns:**

  * `nothing`: `map` field within `mapS` is mutated with IGRF corrected map data

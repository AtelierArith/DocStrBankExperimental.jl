```
map_trim(map_map::Matrix,
         map_xx::Vector    = collect(axes(map_map,2)),
         map_yy::Vector    = collect(axes(map_map,1)),
         pad::Int          = 0,
         xx_lim::Tuple     = (-Inf,Inf),
         yy_lim::Tuple     = (-Inf,Inf),
         zone_utm::Int     = 18,
         is_north::Bool    = true,
         map_units::Symbol = :rad,
         silent::Bool      = true)
```

Trim map by removing large areas that are missing map data. Returns indices for the original map that produces the appropriate trimmed map.

**Arguments:**

  * `map_map`:   `ny` x `nx` 2D gridded map data
  * `map_xx`:    (optional) `nx` map x-direction (longitude) coordinates [rad] or [deg] or [m]
  * `map_yy`:    (optional) `ny` map y-direction (latitude)  coordinates [rad] or [deg] or [m]
  * `pad`:       (optional) minimum padding (grid cells) along map edges
  * `xx_lim`:    (optional) x-direction map limits `(xx_min,xx_max)` [rad] or [deg] or [m]
  * `yy_lim`:    (optional) y-direction map limits `(yy_min,yy_max)` [rad] or [deg] or [m]
  * `zone_utm`:  (optional) UTM zone, only used if `map_units = :utm`
  * `is_north`:  (optional) if true, map is in northern hemisphere, only used if `map_units = :utm`
  * `map_units`: (optional) map xx/yy units {`:rad`,`:deg`,`:utm`}
  * `silent`:    (optional) if true, no print outs

**Returns:**

  * `ind_xx`: `nx` trimmed x-direction map indices
  * `ind_yy`: `ny` trimmed y-direction map indices

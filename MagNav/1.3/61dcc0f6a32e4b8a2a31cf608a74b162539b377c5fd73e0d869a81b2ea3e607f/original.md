```
map_combine(mapS_vec::Vector, mapS_fallback::MapS = get_map(namad);
            map_info::String   = "Combined map",
            N_levels::Int      = 3,
            dx                 = get_step(mapS_vec[1].xx),
            dy                 = get_step(mapS_vec[1].yy),
            xx_lim::Tuple      = get_lim(mapS_vec[1].xx,0.5),
            yy_lim::Tuple      = get_lim(mapS_vec[1].yy,0.5),
            α                  = 200,
            use_fallback::Bool = true)
```

Combine maps at different altitudes. Lowest and highest maps are directly used (with resampling & resizing), with intermediate maps determined by `N_levels`.

**Arguments:**

  * `mapS_vec`:      vector of `MapS` scalar magnetic anomaly map structs
  * `mapS_fallback`: (optional) fallback `MapS` scalar magnetic anomaly map struct
  * `map_info`:      (optional) map information
  * `N_levels`:      (optional) number of map altitude levels
  * `dx`:            (optional) desired x-direction map step size
  * `dy`:            (optional) desired y-direction map step size
  * `xx_lim`:        (optional) length-`2`x-direction map limits `(xx_min,xx_max)`
  * `yy_lim`:        (optional) length-`2` y-direction map limits `(yy_min,yy_max)`
  * `α`:             (optional) regularization parameter for downward continuation
  * `use_fallback`:  (optional) if true, use `mapS_fallback` for missing map data

**Returns:**

  * `mapS3D`: `MapS3D` 3D (multi-level) scalar magnetic anomaly map struct

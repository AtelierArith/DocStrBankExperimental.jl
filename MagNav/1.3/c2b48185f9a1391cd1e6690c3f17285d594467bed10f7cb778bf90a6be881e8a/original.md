```
map_combine(mapS::MapS, mapS_fallback::MapS = get_map(namad);
            map_info::String = mapS.info,
            xx_lim::Tuple    = get_lim(mapS.xx,0.1),
            yy_lim::Tuple    = get_lim(mapS.yy,0.1),
            α                = 200)
```

Combine two maps at same altitude.

**Arguments:**

  * `mapS`:          `MapS` scalar magnetic anomaly map struct
  * `mapS_fallback`: (optional) fallback `MapS` scalar magnetic anomaly map struct
  * `map_info`:      (optional) map information
  * `xx_lim`:        (optional) length-`2` x-direction map limits `(xx_min,xx_max)`
  * `yy_lim`:        (optional) length-`2` y-direction map limits `(yy_min,yy_max)`
  * `α`:             (optional) regularization parameter for downward continuation

**Returns:**

  * `mapS`: `MapS` scalar magnetic anomaly map struct, combined

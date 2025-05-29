```
ottawa_area_maps(f::Union{String,Symbol} = "")
```

Magnetic anomaly maps near Ottawa, Ontario, Canada, contains:

  * `Eastern_395.h5`:   Eastern Ontario at 395 m HAE
  * `Eastern_drape.h5`: Eastern Ontario on drape
  * `Renfrew_395.h5`:   Renfrew at 395 m HAE
  * `Renfrew_555.h5`:   Renfrew at 555 m HAE
  * `Renfrew_drape.h5`: Renfrew on drape
  * `HighAlt_5181.h5`:  High Altitude mini-survey (within Renfrew) at 5181 m HAE
  * `Perth_800.h5`:     Perth mini-survey (within Eastern Ontario) at 800 m HAE

`NOTE`: Missing map data within each map has been filled in (using k-nearest neighbors) so that the maps are fully filled. Care must be taken to not navigate in the filled-in areas, as this is not real data and only done for more accurate and consistent upward continuation of the maps. Use the `map_check` function with the desired map and flight path data to check if the map may be used without navigating into filled-in (artificial) areas.

**Arguments:**

  * `f`: (optional) name of data file (`.h5` extension optional)

**Returns:**

  * `p`: path of folder or `f` data file

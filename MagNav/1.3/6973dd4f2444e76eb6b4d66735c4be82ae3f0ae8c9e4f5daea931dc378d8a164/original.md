```
plot_map!(p1::Plot, mapS::Union{MapS,MapSd,MapS3D};
          use_mask::Bool       = true,
          clims::Tuple         = (),
          dpi::Int             = 200,
          margin::Int          = 2,
          Nmax::Int            = 6*dpi,
          legend::Bool         = true,
          axis::Bool           = true,
          map_color::Symbol    = :usgs,
          bg_color::Symbol     = :white,
          map_units::Symbol    = :rad,
          plot_units::Symbol   = :deg
          b_e::AbstractBackend = gr())
```

Plot map on an existing plot.

**Arguments:**

  * `p1`:         plot
  * `mapS`:       `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct
  * `use_mask`:   (optional) if true, apply `mapS` mask to map
  * `clims`:      (optional) length-`2` colorbar limits `(cmin,cmax)`
  * `dpi`:        (optional) dots per inch (image resolution)
  * `margin`:     (optional) margin around plot [mm]
  * `Nmax`:       (optional) maximum number of data points plotted (per axis)
  * `legend`:     (optional) if true, show legend
  * `axis`:       (optional) if true, show axes
  * `map_color`:  (optional) filled contour color scheme {`:usgs`,`:gray`,`:gray1`,`:gray2`,`:plasma`,`:magma`}
  * `bg_color`:   (optional) background color
  * `map_units`:  (optional) map  xx/yy units {`:rad`,`:deg`}
  * `plot_units`: (optional) plot xx/yy units {`:rad`,`:deg`,`:m`}
  * `b_e`:        (optional) plotting backend

**Returns:**

  * `nothing`: map is plotted on `p1`

```
plot_map!(p1::Plot, map_map::Matrix,
          map_xx::Vector       = [],
          map_yy::Vector       = [];
          clims::Tuple         = (),
          dpi::Int             = 200,
          margin::Int          = 2,
          Nmax::Int            = 6*dpi,
          legend::Bool         = true,
          axis::Bool           = true,
          map_color::Symbol    = :usgs,
          bg_color::Symbol     = :white,
          map_units::Symbol    = :rad,
          plot_units::Symbol   = :deg,
          b_e::AbstractBackend = gr())
```

Plot map on an existing plot.

**Arguments:**

  * `p1`:         plot
  * `map_map`:    `ny` x `nx` 2D gridded map data
  * `map_xx`:     `nx` map x-direction (longitude) coordinates [rad] or [deg]
  * `map_yy`:     `ny` map y-direction (latitude)  coordinates [rad] or [deg]
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

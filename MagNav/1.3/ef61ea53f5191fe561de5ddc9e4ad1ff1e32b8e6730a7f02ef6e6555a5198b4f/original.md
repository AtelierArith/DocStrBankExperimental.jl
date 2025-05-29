```
plot_mag_map(path::Path, mag, itp_mapS;
             lab::String        = "magnetometer",
             order::Symbol      = :magmap,
             dpi::Int           = 200,
             Nmax::Int          = 5000,
             detrend_data::Bool = true,
             show_plot::Bool    = true,
             save_plot::Bool    = false,
             plot_png::String   = "mag_vs_map.png")
```

Plot scalar magnetometer measurements vs map values.

**Arguments:**

  * `path`:         `Path` struct, i.e., `Traj` trajectory struct, `INS` inertial navigation system struct, or `FILTout` filter extracted output struct
  * `mag`:          scalar magnetometer measurements [nT]
  * `itp_mapS`:     scalar map interpolation function (`f(lat,lon)` or `f(lat,lon,alt)`)
  * `lab`:          (optional) magnetometer data (legend) label
  * `order`:        (optional) plotting order {`:magmap`,`:mapmag`}
  * `dpi`:          (optional) dots per inch (image resolution)
  * `Nmax`:         (optional) maximum number of data points plotted
  * `detrend_data`: (optional) if true, detrend plot data
  * `show_plot`:    (optional) if true, show `p1`
  * `save_plot`:    (optional) if true, save `p1` as `plot_png`
  * `plot_png`:     (optional) plot file name to save (`.png` extension optional)

**Returns:**

  * `p1`: scalar magnetometer measurements vs map values

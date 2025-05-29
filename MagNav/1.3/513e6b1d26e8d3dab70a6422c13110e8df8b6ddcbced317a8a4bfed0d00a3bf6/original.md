```
plot_filt(p1::Plot, traj::Traj, ins::INS, filt_out::FILTout;
          dpi::Int        = 200,
          Nmax::Int       = 5000,
          plot_vel::Bool  = false,
          show_plot::Bool = true,
          save_plot::Bool = false)
```

Plot flights paths on an existing plot and latitudes & longitudes vs time.

**Arguments:**

  * `p1`:        plot (i.e., map)
  * `traj`:      `Traj` trajectory struct
  * `ins`:       `INS` inertial navigation system struct
  * `filt_out`:  `FILTout` filter extracted output struct
  * `dpi`:       (optional) dots per inch (image resolution)
  * `Nmax`:      (optional) maximum number of data points plotted
  * `plot_vel`:  (optional) if true, plot velocities
  * `show_plot`: (optional) if true, show plots
  * `save_plot`: (optional) if true, save plots with default file names

**Returns:**

  * `p2`: `p1` with flight paths
  * `p3`: latitudes  vs time
  * `p4`: longitudes vs time
  * `p5`: if `plot_vel = true`, north velocities vs time
  * `p6`: if `plot_vel = true`, east  velocities vs time

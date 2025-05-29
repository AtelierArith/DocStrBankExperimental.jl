```
plot_filt_err(traj::Traj, filt_out::FILTout, crlb_out::CRLBout;
              dpi::Int        = 200,
              Nmax::Int       = 5000,
              plot_vel::Bool  = false,
              show_plot::Bool = true,
              save_plot::Bool = false)
```

Plot northing & easting errors vs time.

**Arguments:**

  * `traj`:      `Traj` trajectory struct
  * `filt_out`:  `FILTout` filter extracted output struct
  * `crlb_out`:  `CRLBout` Cramér–Rao lower bound extracted output struct
  * `dpi`:       (optional) dots per inch (image resolution)
  * `Nmax`:      (optional) maximum number of data points plotted
  * `plot_vel`:  (optional) if true, plot velocity errors
  * `show_plot`: (optional) if true, show plots
  * `save_plot`: (optional) if true, save plots with default file names

**Returns:**

  * `p1`: northing errors vs time
  * `p2`: easting  errors vs time
  * `p3`: if `plot_vel = true`, north velocity errors vs time
  * `p4`: if `plot_vel = true`, east  velocity errors vs time

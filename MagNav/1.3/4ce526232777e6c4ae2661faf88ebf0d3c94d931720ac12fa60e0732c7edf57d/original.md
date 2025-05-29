```
plot_filt!(p1::Plot, traj::Traj, ins::INS, filt_out::FILTout;
           dpi::Int        = 200,
           Nmax::Int       = 5000,
           show_plot::Bool = true,
           save_plot::Bool = false)
```

Plot flights paths on an existing plot.

**Arguments:**

  * `p1`:        plot (i.e., map)
  * `traj`:      `Traj` trajectory struct
  * `ins`:       `INS` inertial navigation system struct
  * `filt_out`:  `FILTout` filter extracted output struct
  * `dpi`:       (optional) dots per inch (image resolution)
  * `Nmax`:      (optional) maximum number of data points plotted
  * `show_plot`: (optional) if true, show plots
  * `save_plot`: (optional) if true, save plots with default file names

**Returns:**

  * `nothing`: flight paths are plotted on `p1`

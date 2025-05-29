```
plot_correlation(xyz::XYZ,
                 xfeature::Symbol = :mag_1_c,
                 yfeature::Symbol = :mag_1_uc,
                 ind              = trues(xyz.traj.N);
                 lim::Real        = 0,
                 dpi::Int         = 200,
                 show_plot::Bool  = true,
                 save_plot::Bool  = false,
                 plot_png::String = "$xfeature-$yfeature.png",
                 silent::Bool     = true)
```

Plot the correlation between 2 features.

**Arguments:**

  * `xyz`:       `XYZ` flight data struct
  * `xfeature`:  x-axis feature name
  * `yfeature`:  y-axis feature name
  * `ind`:       (optional) selected data indices
  * `lim`:       (optional) only plot if Pearson correlation coefficient > `lim`
  * `dpi`:       (optional) dots per inch (image resolution)
  * `show_plot`: (optional) if true, show `p1`
  * `save_plot`: (optional) if true, save `p1` as `plot_png`
  * `plot_png`:  (optional) plot file name to save (`.png` extension optional)
  * `silent`:    (optional) if true, no print outs

**Returns:**

  * `p1`: plot of `yfeature` vs `xfeature` correlation

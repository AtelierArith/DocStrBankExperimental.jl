```
plot_mag(xyz::XYZ;
         ind                       = trues(xyz.traj.N),
         detrend_data::Bool        = false,
         use_mags::Vector{Symbol}  = [:all_mags],
         vec_terms::Vector{Symbol} = [:all],
         ylim::Tuple               = (),
         dpi::Int                  = 200,
         show_plot::Bool           = true,
         save_plot::Bool           = false,
         plot_png::String          = "scalar_mags.png")
```

Plot scalar or vector (fluxgate) magnetometer data from a given flight test.

**Arguments:**

  * `xyz`:          `XYZ` flight data struct
  * `ind`:          (optional) selected data indices
  * `detrend_data`: (optional) if true, detrend plot data
  * `use_mags`:     (optional) scalar or vector (fluxgate) magnetometers to plot {`:all_mags`, `:comp_mags` or `:mag_1_c`, `:mag_1_uc`, `:flux_a`, etc.}

      * `:all_mags`  = all provided scalar magnetometer fields (e.g., `:mag_1_c`, `:mag_1_uc`, etc.)
      * `:comp_mags` = provided compensation(s) between `:mag_1_uc` & `:mag_1_c`, etc.
  * `vec_terms`:    (optional) vector magnetometer (fluxgate) terms to plot {`:all` or `:x`,`:y`,`:z`,`:t`}
  * `ylim`:         (optional) length-`2` plot `y` limits (`ymin`,`ymax`) [nT]
  * `dpi`:          (optional) dots per inch (image resolution)
  * `show_plot`:    (optional) if true, show `p1`
  * `save_plot`:    (optional) if true, save `p1` as `plot_png`
  * `plot_png`:     (optional) plot file name to save (`.png` extension optional)

**Returns:**

  * `p1`: plot of scalar or vector (fluxgate) magnetometer data

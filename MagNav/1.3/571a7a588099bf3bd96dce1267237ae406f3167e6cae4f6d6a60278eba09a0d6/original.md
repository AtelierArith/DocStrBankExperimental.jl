```
plot_mag_c(xyz::XYZ,xyz_comp::XYZ;
           ind                      = trues(xyz.traj.N),
           ind_comp                 = trues(xyz_comp.traj.N),
           detrend_data::Bool       = true,
           λ                        = 0.025,
           terms                    = [:permanent,:induced,:eddy],
           pass1                    = 0.1,
           pass2                    = 0.9,
           fs                       = 10.0,
           use_mags::Vector{Symbol} = [:all_mags],
           use_vec::Symbol          = :flux_a,
           plot_diff::Bool          = false,
           plot_mag_1_uc::Bool      = true,
           plot_mag_1_c::Bool       = true,
           ylim                     = (),
           dpi::Int                 = 200,
           show_plot::Bool          = true,
           save_plot::Bool          = false,
           plot_png::String         = "scalar_mags_comp.png")
```

Plot compensated magnetometer(s) data from a given flight test. Assumes Mag 1 (i.e., `:mag_1_uc` & `:mag_1_c`) is the best magnetometer (i.e., stinger).

**Arguments:**

  * `xyz`:           `XYZ` flight data struct
  * `xyz_comp`:      `XYZ` flight data struct to use for compensation
  * `ind`:           (optional) selected data indices
  * `ind_comp`:      (optional) selected data indices to use for compensation
  * `detrend_data`:  (optional) if true, detrend plot data
  * `λ`:             (optional) ridge parameter
  * `terms`:         (optional) Tolles-Lawson terms to use {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `pass1`:         (optional) filter first passband frequency [Hz]
  * `pass2`:         (optional) filter second passband frequency [Hz]
  * `fs`:            (optional) filter sampling frequency [Hz]
  * `use_mags`:      (optional) scalar or vector (fluxgate) magnetometers to plot {`:all_mags`, or `:mag_1_uc`, etc.}

      * `:all_mags` = all uncompensated scalar magnetometer fields (e.g., `:mag_1_uc`, etc.)
  * `use_vec`:       (optional) vector magnetometer (fluxgate) to use for Tolles-Lawson `A` matrix {`:flux_a`, etc.}
  * `plot_diff`:     (optional) if true, plot difference between `provided` compensated data & compensated mags `as performed here`
  * `plot_mag_1_uc`: (optional) if true, plot mag*1*uc (uncompensated mag_1)
  * `plot_mag_1_c`:  (optional) if true, plot mag*1*c (compensated mag_1)
  * `ylim`:          (optional) length-`2` plot `y` limits (`ymin`,`ymax`) [nT]
  * `dpi`:           (optional) dots per inch (image resolution)
  * `show_plot`:     (optional) if true, show `p1`
  * `save_plot`:     (optional) if true, save `p1` as `plot_png`
  * `plot_png`:      (optional) plot file name to save (`.png` extension optional)

**Returns:**

  * `p1`: plot of compensated magnetometer data

```
plot_correlation_matrix(xyz::XYZ, ind = trues(xyz.traj.N),
                        features_setup::Vector{Symbol} = [:mag_1_uc,:TL_A_flux_a];
                        terms             = [:permanent],
                        sub_diurnal::Bool = false,
                        sub_igrf::Bool    = false,
                        bpf_mag::Bool     = false,
                        dpi::Int          = 200,
                        Nmax::Int         = 1000,
                        show_plot::Bool   = true,
                        save_plot::Bool   = false,
                        plot_png::String  = "correlation_matrix.png")
```

Plot the correlation matrix for `2-5` features.

**Arguments:**

  * `xyz`:            `XYZ` flight data struct
  * `ind`:            selected data indices
  * `features_setup`: vector of features to include
  * `terms`:          (optional) Tolles-Lawson terms to use {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `sub_diurnal`:    (optional) if true, subtract diurnal from scalar magnetometer measurements
  * `sub_igrf`:       (optional) if true, subtract IGRF from scalar magnetometer measurements
  * `bpf_mag`:        (optional) if true, bpf scalar magnetometer measurements
  * `dpi`:            (optional) dots per inch (image resolution)
  * `Nmax`:           (optional) maximum number of data points plotted
  * `show_plot`:      (optional) if true, show `p1`
  * `save_plot`:      (optional) if true, save `p1` as `plot_png`
  * `plot_png`:       (optional) plot file name to save (`.png` extension optional)

**Returns:**

  * `p1`: plot of correlation matrix between `features` (created from `features_setup`)

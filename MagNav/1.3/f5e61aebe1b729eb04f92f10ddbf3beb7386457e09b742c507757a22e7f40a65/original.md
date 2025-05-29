```
plot_frequency(xyz::XYZ;
               ind                = trues(xyz.traj.N),
               field::Symbol      = :mag_1_uc,
               freq_type::Symbol  = :PSD,
               detrend_data::Bool = true,
               window::Function   = hamming,
               dpi::Int           = 200,
               show_plot::Bool    = true,
               save_plot::Bool    = false,
               plot_png::String   = "PSD.png")
```

Plot frequency data, either Welch power spectral density (PSD) or spectrogram.

**Arguments:**

  * `xyz`:          `XYZ` flight data struct
  * `ind`:          (optional) selected data indices
  * `field`:        (optional) data field in `xyz` to plot
  * `freq_type`:    (optional) frequency plot type {`:PSD`,`:psd`,`:spectrogram`,`:spec`}
  * `detrend_data`: (optional) if true, detrend plot data
  * `window`:       (optional) type of window used
  * `dpi`:          (optional) dots per inch (image resolution)
  * `show_plot`:    (optional) if true, show `p1`
  * `save_plot`:    (optional) if true, save `p1` as `plot_png`
  * `plot_png`:     (optional) plot file name to save (`.png` extension optional)

**Returns:**

  * `p1`: plot of Welch power spectral density (PSD) or spectrogram

```
plot_basic(tt::Vector, y::Vector, ind = trues(length(tt));
           lab::String      = "",
           xlab::String     = "time [min]",
           ylab::String     = "",
           show_plot::Bool  = true,
           save_plot::Bool  = false,
           plot_png::String = "data_vs_time.png")
```

Plot data vs time.

**Arguments:**

  * `tt`:        length-`N` time vector [s]
  * `y`:         length-`N` data vector
  * `ind`:       (optional) selected data indices
  * `lab`:       (optional) data (legend) label
  * `xlab`:      (optional) x-axis label
  * `ylab`:      (optional) y-axis label
  * `show_plot`: (optional) if true, show `p1`
  * `save_plot`: (optional) if true, save `p1` as `plot_png`
  * `plot_png`:  (optional) plot file name to save (`.png` extension optional)

**Returns:**

  * `p1`: plot of `y` vs `tt`

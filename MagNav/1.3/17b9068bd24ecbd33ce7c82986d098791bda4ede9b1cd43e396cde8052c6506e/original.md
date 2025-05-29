```
plot_autocor(x::Vector, dt = 0.1, dt_max = 300.0;
             show_plot::Bool  = true,
             save_plot::Bool  = false,
             plot_png::String = "autocor.png")
```

Plot autocorrelation of data (e.g., actual - expected measurements). Prints out `σ` = standard deviation & `τ` = autocorrelation decay to e^-1 of `x`.

**Arguments:**

  * `x`:         data vector
  * `dt`:        (optional) measurement time step [s]
  * `dt_max`:    (optional) maximum time step to evaluate [s]
  * `show_plot`: (optional) if true, show `p1`
  * `save_plot`: (optional) if true, save `p1` as `plot_png`
  * `plot_png`:  (optional) plot file name to save (`.png` extension optional)

**Returns:**

  * `p1`: plot of autocorrelation of `x`

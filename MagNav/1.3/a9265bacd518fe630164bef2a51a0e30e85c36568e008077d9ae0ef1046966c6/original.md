```
plot_events!(p1::Plot, t::Real, lab::String = "";
             legend::Symbol = :outertopright)
```

Plot in-flight event on an existing plot.

**Arguments:**

  * `p1`:     plot (i.e., time series of data)
  * `t`:      time of in-flight event
  * `lab`:    (optional) in-flight event (legend) label
  * `legend`: (optional) legend position (e.g., `:topleft`,`:outertopright`)

**Returns:**

  * `nothing`: in-flight event is plotted on `p1`

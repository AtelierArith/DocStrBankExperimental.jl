```
plot_events!(p1::Plot, flight::Symbol,  df_event::DataFrame;
             keyword::String = "",
             show_lab::Bool  = true,
             t0::Real        = 0,
             t_units::Symbol = :sec,
             legend::Symbol  = :outertopright)
```

Plot in-flight event(s) on an existing plot.

**Arguments:**

  * `p1`:       plot (i.e., time series of data)
  * `flight`:   flight name (e.g., `:Flt1001`)
  * `df_event`: lookup table (DataFrame) of in-flight events

| **Field** | **Type** | **Description**                |
|:--------- |:-------- |:------------------------------ |
| `flight`  | `Symbol` | flight name (e.g., `:Flt1001`) |
| `tt`      | `Real`   | time of `event` [s]            |
| `event`   | `String` | event description              |

  * `keyword`:  (optional) keyword to search within events, case insensitive
  * `show_lab`: (optional) if true, show in-flight event (legend) label(s)
  * `t0`:       (optional) time offset [`t_units`]
  * `t_units`:  (optional) time units {`:sec`,`:min`}
  * `legend`:   (optional) legend position (e.g., `:topleft`,`:outertopright`)

**Returns:**

  * `nothing`: in-flight events are plotted on `p1`

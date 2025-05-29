```
wiggle_plot(image, xrec, time_axis; t_scale=1.5,
            new_fig=true)
```

wiggle_plot of a seismic traces.

# Arguments

  * `image::Array{T, 2}`: Shot record to be plotted
  * `xrec::Array{T, 1}`: Receiver coordinates
  * `time_axis::Array{T, 1}`: Time axis
  * `t_scale::Float`: (Optional) Time scaling, default=1.5. Applied scaling is `(1:max_time).^t_scale`.
  * `new_fig::Bool`: (Optional) Create a new figure, default=true

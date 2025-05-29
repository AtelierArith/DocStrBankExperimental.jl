```
mk_gif(data, title="", xlabel="time, t", 
             ylabel="output, y(t)",
             savename="response")
```

make a .gif of the process response. `data` is a data frame with two columns, `:t` and `:output`, likely returned from [`simulate`](@ref). accepts same arguments as [`viz_response`](@ref). ImageMagick must be installed to create the .gif. the .gif is saved as a file `savename`.

# Arguments

  * `data::DataFrame`: data frame of time series data, containing a `:t` column for times and `:output` column for the outputs.
  * `title::String`: title of plot
  * `xlabel::String`: x-label
  * `ylabel::String`: y-label
  * `savename::String`: filename to save as a .gif. .gif extension automatically appended if not provided.

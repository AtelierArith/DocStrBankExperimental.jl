Processor for plotting the solution in real time.

Keyword arguments:

  * `plot`: Plot function.
  * `nupdate`: Show solution every `nupdate` time step.
  * `displayfig`: Display the figure at the start.
  * `screen`: If `nothing`, use default display.   If `GLMakie.screen()` multiple plots can be displayed in separate   windows like in MATLAB (see also `GLMakie.closeall()`).
  * `displayupdates`: Display the figure at every update (if using CairoMakie).
  * `sleeptime`: The `sleeptime` is slept at every update, to give Makie   time to update the plot. Set this to `nothing` to skip sleeping.

Additional `kwargs` are passed to the `plot` function.

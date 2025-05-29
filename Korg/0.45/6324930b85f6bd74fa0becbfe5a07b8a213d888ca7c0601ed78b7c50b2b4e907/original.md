```
prune_linelist(atm, linelist, A_X, wls...; threshold=1.0, sort=true, synthesis_kwargs...)
```

Return the vector containing the strongest lines in  `linelist`, (optionally) sorted by approximate equivalent width.

# Arguments

  * `atm`: the atmosphere model
  * `linelist`: the linelist (a vector of `Line` objects)
  * `A_X`: the abundance of each element (see [`format_A_X`](@ref))
  * `wls...`: the wavelength ranges to synthesize over.  These are specified the same way as the `wls` for [`synthesize`](@ref).

# Keyword Arguments

  * `threshold=0.1`: The threshold ratio in the line center absorption to the continuum absorption computed at the photosphere for a line to be included in the returned list. `0.1` is a reasonable default for getting a sense of what might be measurable in a high-res, high-quality spectrum, but it should not be used to create a linelist for synthesis.
  * `sort_by_EW=true`: If `true`, the returned linelist will be sorted by approximate reduced equivalent width.  If `false`, the linelist will be in wavelength order. Leaving the list in wavelength order is much faster, but sorting by strength is useful for visualizing the strongest lines.
  * `verbose=true`: If `true`, a progress bar will be displayed while measuring the EWs. All other kwargs are passed to internal calls to [`synthesize`](@ref).
  * `max_distance=0.0`, how far from `wls` lines can be (in Å) before they are excluded from the returned list.

!!! caution
    While this function can be used to prune a linelist for synthesis, the default behavior too aggressive for this purpose.  Set a much lower threshold (e.g. `threshold=1e-4`) and use `sort_by_EW=false` if you are pruning the linelist to speedup synthesis.  Note that Korg will dynamically choose which lines to include even if you use a large linelist (see the `line_cutoff_threshold` keyword argument to [`synthesize`](@ref)).


See also [`merge_close_lines`](@ref) if you are using this for plotting.

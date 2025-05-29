```
Resampler(matrix; max_resolution=automatic, method=Interpolations.Linear(), update_while_button_pressed=false)
```

Creates a resampling type which can be used with `heatmap`, to display large images/heatmaps. Passed can be any array that supports `array(linrange, linrange)`, as the interpolation interface from Interpolations.jl. If the array doesn't support this, it will be converted to an interpolation object via: `Interpolations.interpolate(data, Interpolations.BSpline(method))`.

  * `max_resolution` can be set to `automatic` to use the full resolution of the screen, or a tuple/integer of the desired resolution.
  * `method` is the interpolation method used, defaulting to `Interpolations.Linear()`.
  * `update_while_button_pressed` will update the heatmap while a mouse button is pressed, useful for zooming/panning. Set it to false for e.g. WGLMakie to avoid updating while dragging.
  * `lowres_background` will always show a low resolution background while the high resolution image is being calculated.

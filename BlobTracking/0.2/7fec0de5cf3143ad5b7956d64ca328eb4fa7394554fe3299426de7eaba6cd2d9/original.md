```
showblobs(img::AbstractMatrix{T}, result::TrackingResult, m::Measurement; rad=8, recorder=nothing, display=true) where T
```

Overlay found blobs on `img`

#Arguments:

  * `img`: an image
  * `result`: a `TrackingResult`
  * `m`: a `Measurement`
  * `rad`: radius of blobs to draw
  * `recorder`: an optional `Recorder`
  * `display = Base.display`: function to display image. Use `display=nothing` to not display.

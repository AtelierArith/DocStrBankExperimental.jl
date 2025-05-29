```
colorbuffer(scene, format::ImageStorageFormat = JuliaNative; update=true, backend=current_backend(), screen_config...)
```

Returns the content of the given scene or screen rasterised to a Matrix of Colors. The return type is backend-dependent, but will be some form of RGB or RGBA.

  * `backend::Module`: A module which is a Makie backend.  For example, `backend = GLMakie`, `backend = CairoMakie`, etc.
  * `format = JuliaNative` : Returns a buffer in the format of standard julia images (dims permuted and one reversed)
  * `format = GLNative` : Returns a more efficient format buffer for GLMakie which can be directly                       used in FFMPEG without conversion
  * `screen_config`: Backend dependent, look up via `?Backend.Screen`/`Base.doc(Backend.Screen)`
  * `update=true`: resets/updates limits. Set to false, if you want to preserver camera movements.

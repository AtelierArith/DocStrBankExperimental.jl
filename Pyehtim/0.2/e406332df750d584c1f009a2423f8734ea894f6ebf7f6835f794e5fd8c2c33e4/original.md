```
load_uvfits_and_array(uvfile, arrayfile=nothing; kwargs...)
```

Load a uvfits file with eht-imaging and returns a eht-imaging `Obsdata` object. You can optionally pass an array file as well that will load additional information such at the telescopes field rotation information with the arrayfile. This is expected to be an eht-imaging produced array or antenna file.

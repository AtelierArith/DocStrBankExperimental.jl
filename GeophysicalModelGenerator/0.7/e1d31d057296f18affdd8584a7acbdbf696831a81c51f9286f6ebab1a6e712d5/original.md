```
movie_from_images(; dir=pwd(), file=nothing, outfile=nothing, framerate=10, copy_to_current_dir=true, type=:mp4_default, collect=true)
```

The typical way to create animations with `Paraview` is to use the `Save Animation` option to save a series of `*.png` images.

This function combines these images to an `*.mp4` movie.

# Optional options

  * `dir`:    directory where the images are stored.
  * `file`:   filename of the image series without extension and numbers. Required if >1 image series is stored in the same directory. By default we reconstruct this name from the available files.
  * `outfile`:  filename of the resulting movie without extension; if not specified, `file` is used.
  * `framerate`: number of frames/second.
  * `copy_to_current_dir`: copies the final movie to the current directory if `true` (default); otherwise it will be stored in `dir`.
  * `type`: type of movie that is created; possible options are:

      * `:mp4_default`: Default option that saves a well-compressed `mp4` movie that works well for us on ipad and embedded in a powerpoint presentation.
      * `:mov_hires`: Higher-resolution quicktime movie (larger filesize & not compatible with windows)
  * `collect`: suppresses output of `FFMPEG` if `true` (default).

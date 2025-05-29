```
ascii_show(stream, img, colordepth::TermColorDepth, encoder::Symbol=:auto, maxsize::Tuple=displaysize(io))
```

Displays the given image `img` using unicode characters and terminal colors. `img` has to be an array of `Colorant`.

  * `maxsize` specifies the maximum numbers of string characters (lines, columns) that should be used for the resulting image. Larger images are downscaled automatically using `restrict`.

If working in the REPL, the function tries to choose the encoding based on the current display size. The image will also be downsampled to fit into the display (using `restrict`).

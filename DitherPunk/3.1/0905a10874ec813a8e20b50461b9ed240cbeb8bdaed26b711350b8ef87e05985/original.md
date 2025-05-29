```
braille(img; kwargs...)
braille(img, alg; kwargs...)
```

Binary dither with algorithm `alg`, then print image in braille.

## Keyword arguments

  * `invert`: invert Unicode output, defaults to `false`
  * `to_string`: return a string instead of printing to terminal. Defaults to `false`.
  * `method`: method used to print in unicode. Either `:braille` or `:block`. Defaults to `:braille`.

All keyword arguments for binary dithering methods can be used.

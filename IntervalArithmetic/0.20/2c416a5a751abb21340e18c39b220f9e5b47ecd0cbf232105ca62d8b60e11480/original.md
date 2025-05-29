```
setformat(format=none; decorations=none, sigfigs=none)
```

`setformat` changes how intervals are displayed. It returns the new `DisplayParameters` object.

Note that The `@format` macro is more user-friendly.

The following options are available:

  * `format`: interval output format

      * `:standard`: `[1, 2]`
      * `:full`: `Interval(1, 2)`
      * `:midpoint`: 1.5 ± 0.5
  * `sigfigs`: number of significant figures to show in `standard` mode; the default is 6
  * `decorations` (boolean):  show decorations or not

Example:

```
julia> setformat(:full, decorations=true)
Display parameters:
- format: full
- decorations: true
- significant figures: 6
```

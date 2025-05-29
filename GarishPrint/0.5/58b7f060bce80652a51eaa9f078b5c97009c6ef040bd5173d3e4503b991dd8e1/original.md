```
pprint([io::IO=stdout], [mimetype], x; kw...)
```

Pretty print an object `x` to `io`, default `io` is `stdout`.

!!! note
    `pprint` will detect if an object type has overloaded `Base.show`, and use that if possible, overloading `Base.show` to `GarishPrint` for custom type should use [`pprint_struct`](@ref) to avoid recursive call into `Base.show`.


# Keyword Arguments

  * `indent::Int`: indent size, default is `2`.
  * `compact::Bool`: whether print withint one line, default is `get(io, :compact, false)`.
  * `limit::Bool`: whether the print is limited, default is `get(io, :compact, false)`.
  * `displaysize::Tuple{Int, Int}`: the displaysize hint of printed string, note this is not stricted obeyed,

default is `displaysize(io)`.

  * `show_indent::Bool`: whether print indentation hint, default is `true`.
  * `color::Bool`: whether print with color, default is `true`.

## Keyword Arguments for option struct defined by Configurations

  * `include_defaults::Bool`: whether print the default values,   default is `false` to provide more compact printing in REPL.

## Color Preference

color preference is available as keyword arguments to override the default color scheme. These arguments may take any of the values `:normal`, `:default`, `:bold`, `:black`, `:blink`, `:blue`, `:cyan`, `:green`, `:hidden`, `:light_black`, `:light_blue`, `:light_cyan`, `:light_green`, `:light_magenta`, `:light_red`, `:light_yellow`, `:magenta`, `:nothing`, `:red`, `:reverse`, `:underline`, `:white`, or `:yellow` or an integer between 0 and 255 inclusive. Note that not all terminals support 256 colors.

The default color scheme can be checked via `GarishPrint.default_colors_256()` for 256 color, and `GarishPrint.default_colors_ansi()` for ANSI color. The 256 color will be used when the terminal is detected to support 256 color.

  * `fieldname`: field name of a struct.
  * `type`: the color of a type.
  * `operator`: the color of an operator, e.g `+`, `=>`.
  * `literal`: the color of literals.
  * `constant`: the color of constants, e.g `π`.
  * `number`: the color of numbers, e.g `1.2`, `1`.
  * `string`: the color of string.
  * `comment`: comments, e.g `# some comments`
  * `undef`: the const binding to `UndefInitializer`
  * `linenumber`: line numbers.

# Notes

The color print and compact print can also be turned on/off by setting `IOContext`, e.g `IOContext(io, :color=>false)` will print without color, and `IOContext(io, :compact=>true)` will print within one line. This is also what the standard Julia `IO` objects follows in printing by default.

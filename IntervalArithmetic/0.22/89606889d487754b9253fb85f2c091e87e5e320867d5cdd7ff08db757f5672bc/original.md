```
setdisplay(format::Symbol; decorations::Bool, ng_flag::Bool, sigdigits::Int)
```

Change the format used by `show` to display intervals.

Possible options:

  * `format` can be:

      * `:infsup`: display intervals as `[a, b]`.
      * `:midpoint`: display intervals as `m ± r`.
      * `:full`: display interval bounds entirely, ignoring `sigdigits`.
  * `decorations`: display the decorations or not.
  * `ng_flag`: display the NG flag or not.
  * `sigdigits`: number (greater or equal to 1) of significant digits to display.

Initially, the display options are set to `setdisplay(:infsup; decorations = true, ng_flag = true, sigdigits = 6)`. If any of `format`, `decorations`, `ng_flag` and `sigdigits` is omitted, then their value is left unchanged.

# Examples

```jldoctest
julia> setdisplay(:infsup; decorations = true, sigdigits = 6) # default display options
Display options:
  - format: infsup
  - decorations: true
  - NG flag: true
  - significant digits: 6

julia> x = interval(0.1, 0.3)
[0.0999999, 0.300001]_com

julia> setdisplay(:full)
Display options:
  - format: full
  - decorations: true
  - NG flag: true
  - significant digits: 6 (ignored)

julia> x
Interval{Float64}(0.1, 0.3, com)

julia> setdisplay(:infsup; sigdigits = 3)
Display options:
  - format: infsup
  - decorations: true
  - NG flag: true
  - significant digits: 3

julia> x
[0.0999, 0.301]_com

julia> setdisplay(; decorations = false)
Display options:
  - format: infsup
  - decorations: false
  - NG flag: true
  - significant digits: 3

julia> x
[0.0999, 0.301]
```

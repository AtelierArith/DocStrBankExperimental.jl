```
out = KomaUI(; kwargs...)
```

Launch the Koma's UI.

# Keywords

  * `darkmode`: (`::Bool`, `=true`) define dark mode style for the UI
  * `frame`: (`::Bool`, `=true`) display the upper frame of the Blink window
  * `phantom_mode`: (`::String`, `="2D"`, opts=[`"2D"`, `"3D"`]) load the default phantom as a   2D or 3D brain example
  * `sim`: (`::Dict{String,Any}`, `=Dict{String,Any}()`) simulation parameters dictionary
  * `rec`: (`::Dict{Symbol,Any}`, `=Dict{Symbol,Any}()`) reconstruction parameters dictionary
  * `return_window`: (`::Bool`, `=false`) make the `out` be either 'nothing' or the Blink window,   depending on whether the `return_window` keyword argument is set to true
  * `show_window`: (`::Bool`, `=true`) display the Blink window

# Returns

  * `out`: (`::Nothing` or `::Blink.AtomShell.Window`) returns either 'nothing' or the Blink   window, depending on whether the `return_window` keyword argument is set to true.

# Examples

```julia-repl
julia> KomaUI()
```

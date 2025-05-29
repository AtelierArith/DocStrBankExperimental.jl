```
@using(package_path)
```

Macro to simplify loading of modules taking advantage of precompilation. When called from Main it temporarilty adds the path to LOAD_PATH and loads the module via `using` When called from a different module it includes the module file and uses `using .MyModule`

`package_path` can be used in several ways

  * as a path to a directory containing a module file of the same name   e.g '@using models/MyApp' to load 'models/MyApp/MyApp.jl'
  * as a path to a module (without extension '.jl')   e.g. '@using models/MyApp' to load models/MyApp.jl'
  * as a path to a package directory containing a 'src' directory and module file therein   e.g. '@using models/MyApp' to load 'models/MyApp/src/MyApp.jl'

### Examples

```julia
@using models/MyApp

@using StippleDemos/Vue3/Calendars
```

or explicitly

```julia
@using StippleDemos/Vue3/Calendars/Calendars
```

Note, directories containing special characters like colon (`':'`) or space (`' '`) need to be escaped by double quotes.

```julia
@using "C:/Program Files/Julia/models/Calendars"

# or
@using "C:/Program Files"/Julia/models/Calendars
```

Caveat: Due to precompilation it is not possible to supply variables to the macro. Calls need to supply explicit paths.

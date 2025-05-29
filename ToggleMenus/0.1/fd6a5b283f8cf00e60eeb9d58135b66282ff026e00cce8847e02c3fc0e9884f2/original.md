```
ToggleMenuMaker(header, settings, icons, pagesize=15; kwargs...)
```

Create a template with the defining values of a `ToggleMenu`, which may be called with further arguments to create one.

# Arguments

  * `header`: An `AbstractString`, which should inform the user what the options do, or           a function `header(m::ToggleMenu)::String`.
  * `settings`: A `Vector{Char}`, every element must be unique, and should be easy to             type.  Pressing a key corresponding to one of the settings will toggle             that option directly to that setting.
  * `icons`:  Optional `Vector{Char}` or `Vector{String}`.  If provided, these must           also be unique, and must have the same number of elements as `settings`.           These are used as the selection icons, which will default to `settings`           if none are provided.
  * `pagesize`:  Number of options to display before scrolling.

# Keyword Arguments

  * `braces`:  This may be a tuple of Strings or Chars, defaults to `("[", "]")`.
  * `keypress`:  A second function to run on keypress, only called if the standard              inputs aren't handled.  Signature is `(menu::ToggleMenu, i::UInt32)`,              where `i` is a somewhat funky representation of the character typed,              as provided by [REPL.TerminalMenus](@extref `Menus`).  This              should return `false` unless the menu is completed, in which case,              return `true`.

Other keyword arguments are passed through to [`TerminalMenus.Config`](@extref `REPL.TerminalMenus.Config`), and may be used to configure aspects of menu presentation and behavior.

The `ToggleMenuMaker` is callable to produce a [`ToggleMenu`](@ref).

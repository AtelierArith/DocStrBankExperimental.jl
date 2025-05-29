# InteractiveCodeSearch.jl –- Interactively search Julia code

Julia has `@edit`, `@less`, etc. which are very handy for reading the implementation of functions.  However, you need to specify a "good enough" set of (type) parameters for them to find the location of the code.

Instead, `InteractiveCodeSearch` provides a few macros to interactively choose the code you want to read.

## Features

  * Interactively choose a method signature before opening the code location in your editor.
  * Various ways to search methods, such as: by function name `@search show`, function call expression `@search show(stdout, "hello")`, function call signature `@search show(::IO, ::String)`, module name `@search Base`, argument value `@searchmethods 1`, and argument type `@searchmethods ::Int`.
  * Interactively search history.  It works in IJulia as well.

## Examples

```julia
using InteractiveCodeSearch
@search show             # search method definitions
@searchmethods 1         # search methods defined for integer
@searchhistory           # search history (Julia ≥ 0.7)
```

## Requirements

  * Interactive matching command.  For example:

      * [fzf](https://github.com/junegunn/fzf) (default in terminal)
      * [peco](https://github.com/peco/peco)
      * [percol](https://github.com/mooz/percol)
      * [rofi](https://github.com/DaveDavenport/rofi) (GUI; default in IJulia)

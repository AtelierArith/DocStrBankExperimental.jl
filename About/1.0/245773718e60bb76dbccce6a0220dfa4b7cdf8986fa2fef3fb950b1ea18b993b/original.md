```
about([io::IO], thing)
```

Display information (to `io` if provided) on the particular nature of `thing`, whatever it may be.

This is implemented for a variety of types and objects, with general implementations for:

  * Functions
  * Types
  * Values
  * Modules

Not sure what to make of this? Just try it out 😉

!!! tip "Tip for package developers"
    See the *extended help* for information on how to implement specialised forms for your own objects. Also consider putting specialised display methods in a package extension.


# Extended help

While it is possible to extend `about` by implementing specialised `about(::IO, ::MyThing)` methods, it is better to specialise the two main functions called by the `about` function for values (not a `Function`, `Type`, or `Module`):

  * `memorylayout(::IO, ::MyThing)`
  * `elaboration(::IO, ::MyThing)`

Either or both of these functions can be specialised to customise the display from `about(::IO, ::MyThing)`, and are involved in the output like so:

```julia-repl
julia> about(mything)

[name] [type hierachy] [size]

[memorylayout]

[elaboration (when non-compact)]
```

As can be guessed from the names, it is expected that `memorylayout` prints an informative representation of the memory layout of its argument. See `src/values.jl` within the `About` package source for some examples (just scroll past the initial generic implementation).

Unlike `memorylayout`, the `elaboration` function does not print anything by default, but can be specialised to add extra pieces of useful information that don't relate to the in-memory representation of the object itself.

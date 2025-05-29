```
Scanf.scanf(b::String, f::Scanf.Format, args...)
Scanf.scanf([io::IO,] f::Scanf.Format, args...)
```

Apply a Scanf format object `f` to provided String (1st method), or scan directly from an `io` object (2nd method). See [`@scanf`](@ref) for more details on C `scanf` support. `io` defaults to `stdin`. The args determine the type and default value for the output data.

Return the number of assigned arguments, followed by the assigned output data.

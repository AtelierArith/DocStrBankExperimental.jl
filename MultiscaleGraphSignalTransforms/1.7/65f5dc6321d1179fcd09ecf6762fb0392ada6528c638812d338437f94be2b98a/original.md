```
stem(f; x = 1:length(f[:]), c = :black, ms = 5, shape = :circle, lw = 1)
```

Display a length N discrete sequence data in a stem plot.

# Input Arguments

  * `f`: function values could be a vector or an N x 1 matrix.
  * `x`: default is `1:N`. x values.
  * `c::Symbol`: default is `:black`. Color of the markers.
  * `ms::Number`: default is `5`. Size of markers.
  * `shape::Symbol`: default is `:circle`. Shape of the markers.
  * `lw::Number`: default is `1`. The line width of the stems.
  * `subgplot::Int`: default is `1`. The subplot index.

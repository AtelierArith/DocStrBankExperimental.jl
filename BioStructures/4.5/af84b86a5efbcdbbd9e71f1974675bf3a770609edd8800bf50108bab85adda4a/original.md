```
showcontactmap(contact_map)
showcontactmap(io, contact_map)
```

Print a representation of a `ContactMap` to `stdout`, or a specified `IO` instance.

A fully plotted version can be obtained with `plot(contact_map)` but that requires Plots.jl; `showcontactmap` works without that dependency.

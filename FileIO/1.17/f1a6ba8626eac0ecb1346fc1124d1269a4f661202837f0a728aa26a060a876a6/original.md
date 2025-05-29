```
add_loader(fmt, :Package=>uuid)
add_loader(fmt, [:Package=>uuid, specifiers...])
```

Declare that format `fmt` can be loaded with package `:Package`. Specifiers include `OSX`, `Unix`, `Windows` and `Linux` to restrict usage to particular operating systems.

See also [`add_format`](@ref) which can combine package support with the format declaration.

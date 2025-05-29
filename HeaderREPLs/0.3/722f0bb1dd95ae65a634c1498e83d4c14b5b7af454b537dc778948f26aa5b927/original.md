```
print_header(io::IO, header::CustomHeader)
```

Print `header` to `io`. `header` must be a mutable struct containing a field `nlines`, and before exiting `print_header` should set this field to the number of lines occupied by the display of your header.

While you have to define `print_header`, generally you should not call it directly. If you need to display the header, call `refresh_header`.

```
function create_form(fields::Vector{TUI_FIELD}; ...)
```

Create a new form with the fields `fields`.

# Keywords

  * `newline_overload`: Enable overloading of `REQ_NEW_LINE`.                     (**Default** = `false`)
  * `backspace_overload`: Enable overloading of `REQ_DEL_PREV`.                       (**Default** = `false`)

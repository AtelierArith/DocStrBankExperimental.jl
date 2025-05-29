```
MultiSelectMenu(options::Array{String,1}; pagesize::Int=10)
```

Create a MultiSelectMenu object. Use `request(menu::MultiSelectMenu)` to get user input. `request()` returns a `Set` containing the indices of options that were selected by the user.

# Arguments

  * `options::Array{String, 1}`: Options to be displayed
  * `pagesize::Int=10`: The number of options to be displayed at one time, the menu will scroll if length(options) > pagesize

```
RadioMenu(options::Array{String,1}; pagesize::Int=10)
```

Create a RadioMenu object. Use `request(menu::RadioMenu)` to get user input. `request()` returns an `Int` which is the index of the option selected by the user.

# Arguments

  * `options::Array{String, 1}`: Options to be displayed
  * `pagesize::Int=10`: The number of options to be displayed at one time, the menu will scroll if length(options) > pagesize

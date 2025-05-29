```
Setter()
Setter("initial_value")
```

Creates a pluto interactivity which separates the setter cell from the state cell.

# Usage

```julia
set_a = Setter("initial_value")

# in another cell, extract the inner state from the setter
# such that updates will rerun this cell
a = @get set_a

# in yet another cell use `set_a`
set_a("new_value")

# or use a function syntax to easily access the previous value
set_a() do prev_a
    "$prev_a!!"
end
```

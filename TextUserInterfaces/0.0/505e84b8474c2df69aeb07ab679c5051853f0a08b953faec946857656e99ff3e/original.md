```
function ncurses_color([foreground::Symbol, background::Symbol,] attrs::Int = 0; kwargs...)
```

Return a mask to apply a color format with the foreground color `foreground`, background color `background`, and the attributes `attrs`.

If the pair (`foreground`, `background`) is omitted, then the foreground and background color will not be changed.

# Keywords

  * `bold`: If `true`, then apply bold format mask to `attrs`.         (**Default** = `false`)
  * `underline`: If `true`, then apply underline format mask to `attrs`.              (**Default** = `false`)

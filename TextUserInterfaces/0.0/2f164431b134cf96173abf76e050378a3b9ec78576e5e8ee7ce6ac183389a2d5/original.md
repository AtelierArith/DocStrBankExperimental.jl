```
function create_window(nlines::Integer, ncols::Integer, begin_y::Integer, begin_x::Integer, id::String = ""; bcols::Integer = 0, blines::Integer = 0, border::Bool = true, border_color::Int = -1, title::String = "", title_color::Int = -1)
```

Create a window. The new window size will be `nlines × ncols` and the origin will be placed at `(begin_y, begin_x)` coordinate of the root window. The window ID `id` is used to identify the new window in the global window list.

# Keyword

  * `bcols`: Number of columns in the window buffer. This will be automatically          increased to, at least, fit the viewable part of the window          (`ncols`). (**Default** = 0)
  * `blines`: Number of lines in the window buffer. This will be automatically           increased to, at least, fit the viewable part of the window           (`nlines`). (**Default** = 0)
  * `border`: If `true`, then the window will have a border. (**Default** =           `true`)
  * `border_color`: Color mask that will be used to print the border. See function                 `ncurses_color`. If negative, then the color will not be                 changed. (**Default** = -1)
  * `focusable`: If `true`, then the window can have focus. Otherwise, all focus              request will be rejected. (**Default** = `true`)
  * `title`: The title of the window, which will only be printed if `border` is          `true`. (**Default** = "")
  * `title_color`: Color mask that will be used to print the title. See                function `ncurses_color`. If negative, then the color will not                be changed. (**Default** = -1)

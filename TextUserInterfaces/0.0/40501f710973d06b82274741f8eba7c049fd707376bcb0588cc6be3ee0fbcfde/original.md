```
function set_window_title(win::Window, title::AbstractString; ...)
```

Set the title of the window `win` to `title`.

# Keywords

  * `title_color`: Color mask that will be used to print the title. See                function `ncurses_color`. If negative, then the color will not                be changed. (**Default** = -1)

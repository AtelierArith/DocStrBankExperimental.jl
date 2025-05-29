```
function create_field(height::Int, width::Int, y::Int, x::Int, buffer::String = "", id::String = "", offscreen::Int = 0, nbuffers::Int = 0; ...)
```

Create a field with id `id`, height `height` and width `width`, positioned at `y` and `x` coordinates. The initial buffer string can be set by the variable `buffer`. The number of off-screen rows is set by `offscreen` and the number of buffers `nbuffers`.

# Keywords

  * `color_foreground`: Color mask that will be used in the field foreground. See                     function `ncurses_color`. If negative, then the color will                     not be changed. (**Default** = -1)
  * `color_background`: Color mask that will be used in the field background. See                     function `ncurses_color`. If negative, then the color will                     not be changed. (**Default** = -1)
  * `justification`: Justification of the form. It can be `:l` for left, `:c` for                  center, and `:r` for right. For any other symbol, the left                  justification is used. (**Default** = `:l`)
  * `visible`: If `true`, then the control is visible on the screen.            (**Default** = `true`)
  * `active`: If `true`, then the control is active. (**Default** = `true`)
  * `public`: If `true`, then the data of the field is displayed during entry. For           example, set this to `false` for password fields.           (**Default** = `true`)
  * `edit`: If `true`, then the data of the field can be modified.         (**Default** = `true`)
  * `wrap`: If `true`, then the word will be wrapped in multi-line fields.         (**Default** = `true`)
  * `blank`: If `true`, then entering a character at the first field position          erases the entire fields. (**Default** = `false`)
  * `autoskip`: If `true`, then the field will be automatically skipped when             filled. (**Default** = `false`)
  * `nullok`: If `true`, then the validation is **not** applied to blank fields.           (**Default** = `true`)
  * `passok`: If `true`, then the validation will occur on every exit. Otherwise,           it will only occur when the field is modified.           (**Default** = `false`)
  * `static`: If `true`, then the field is fixed to the initial dimensions.           Otherwise, it will stretch to fit the entered data.           (**Default** = `true`)

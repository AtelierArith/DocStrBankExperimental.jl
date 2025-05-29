```
get_user_option(text::String, options::AbstractVector) -> Int
```

Get the user option. `text` is the information shown to the user and `options` is a vector with the options. This function returns the selection index with respect to `options`, or -1 if the user did not select an option.

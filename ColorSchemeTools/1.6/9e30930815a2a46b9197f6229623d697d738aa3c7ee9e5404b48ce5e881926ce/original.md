```
make_colorscheme(dict;
    length=100,
    category="",
    notes="")
```

Make a new ColorScheme from a dictionary of linear-segment information. Calls `get_linear_segment_color(dict, n)` with `n` for every `length` value between 0 and 1.

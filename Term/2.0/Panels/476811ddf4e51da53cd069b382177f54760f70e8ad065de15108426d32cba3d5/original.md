```
macro nested_panels(layout_call)
```

Macro to automate layout of multiple nested `Panel`. The width of the panels is automatically adjusted based on the depth of eeach nested level.

Uses `fix_layout_width` recursively to add a keyword argument `width` to each `Panel`.

```
title(
    [scene=current_scene(), ], string;
    align = (:center, :bottom), textsize = 30, parent = Scene(), formatter = string, kw...
)
```

Add a title with content `string` to `scene`.  Pass a `Function` to the `formatter` kwarg if the value passed to `string` isn't actually a String.

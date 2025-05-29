```
textoutlines(s::String, pos::Point=O;
    action=:none,
    halign=:left,
    valign=:baseline,
    startnewpath=true)
```

Convert text to polygons and apply `action`. (ToyAPI)

By default this function discards any current path, unless you use `startnewpath=false`

See also `textpath()`. `textpath()` retains Bezier curves, whereas `textoutlines()` returns flattened curves.

TODO Return something more useful than a Boolean.

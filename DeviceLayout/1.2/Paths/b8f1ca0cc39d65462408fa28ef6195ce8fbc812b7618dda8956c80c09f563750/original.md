```
turn!(p::Path, str::String, r::Coordinate, sty::Style=contstyle1(p))
```

Turn a path `p` with direction coded by string `str`:

  * "l": turn by 90° (left)
  * "r": turn by -90° (right)
  * "lrlrllrrll": do those turns in that order

By default, we take the last continuous style in the path.

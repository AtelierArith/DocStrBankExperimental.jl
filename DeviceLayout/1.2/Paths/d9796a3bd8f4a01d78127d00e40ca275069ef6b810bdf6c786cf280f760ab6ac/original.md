```
straight!(p::Path, l::Coordinate, sty::Style=contstyle1(p))
```

Extend a path `p` straight by length `l` in the current direction. By default, we take the last continuous style in the path.

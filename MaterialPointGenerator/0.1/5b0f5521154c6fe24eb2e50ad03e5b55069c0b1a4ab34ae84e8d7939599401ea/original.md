```
polygon2particle(polygon, lpx, lpy)
```

## Description:

Generate structured particles from a given polygon. Note the vertices of the polygon should  be ordered in a **counterclockwise** manner; otherwise, it may lead to incorrect results.  

`lpx` and `lpy` are the space of particles in `x` and `y` directions, respectively.

`polygon` is the polygon, for example, `polygon = [0 0; 2 0; 2 1; 0 1]` means generate structured particles in a rectangle area.

```
find_center(a::Complex, b::Complex, c::Complex)::Complex
```

`find_center(a,b,c)`: Given three points in the complex plane, find the point `z` that is equidistant from all three. If the three points are collinear then return `Inf + Inf*im`.

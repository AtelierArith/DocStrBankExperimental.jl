```
arcintervals(bd::Billiard) -> s
```

Generate a vector `s`, with entries being the delimiters of the arclengths of the obstacles of the billiard. The arclength from `s[i]` to `s[i+1]` is the arclength spanned by the `i`th obstacle.

`s` is used to transform an arc-coordinate `ξ` from local to global and vice-versa. A local `ξ` becomes global by adding `s[i]` (where `i` is the index of current obstacle). A global `ξ` becomes local by subtracting `s[i]`.

See also [`boundarymap`](@ref), [`to_bcoords`](@ref), [`from_bcoords`](@ref).

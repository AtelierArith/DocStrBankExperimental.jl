```
L"..."
```

Creates a `LaTeXString` and is equivalent to `latexstring(raw"...")`, except that `%$` can be used for interpolation.

```jldoctest
julia> L"x = \sqrt{2}"
L"$x = \sqrt{2}$"

julia> L"x = %$(sqrt(2))"
L"$x = 1.4142135623730951$"
```

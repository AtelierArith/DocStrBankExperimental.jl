```
L"..."
```

`LaTeXString`を作成し、`latexstring(raw"...")`と同等ですが、`%$`を使って補間が可能です。

```jldoctest
julia> L"x = \sqrt{2}"
L"$x = \sqrt{2}$"

julia> L"x = %$(sqrt(2))"
L"$x = 1.4142135623730951$"
```

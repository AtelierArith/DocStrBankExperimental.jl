```
isless(x::Run, y::Run)
```

2つのランをその自然なソート順に従って比較します。まず、行が比較され、等しい場合は列の範囲が比較されます。

```jldoctest reg
julia> using Regions

julia> isless(Run(0, 1:10), Run(1, 0:10))
true

julia> isless(Run(1, 1:10), Run(1, 2:10))
true
```

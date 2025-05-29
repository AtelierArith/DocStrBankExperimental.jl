```
StepRange(obj::GapObj)
```

Return the step range converted from the [GAP range](GAP_ref(ref:Ranges)) `obj`, which may have arbitrary step width.

# Examples

```jldoctest
julia> val = GAP.Obj(1:2:11)
GAP: [ 1, 3 .. 11 ]

julia> StepRange(val)
1:2:11

julia> r = StepRange{Int8,Int8}(val)
1:2:11

julia> typeof(r)
StepRange{Int8, Int8}

```

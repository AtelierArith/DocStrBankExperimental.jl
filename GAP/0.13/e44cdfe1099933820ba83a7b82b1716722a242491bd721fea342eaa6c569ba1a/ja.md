```
StepRange(obj::GapObj)
```

[GAP range](GAP_ref(ref:Ranges)) `obj` から変換されたステップ範囲を返します。ステップ幅は任意です。

# 例

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

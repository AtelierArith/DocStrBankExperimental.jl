```
struct OfDegree{D} <: Function
    degree::D
end
```

関数 `d::OfDegree` は `d(t)` が `degree(t) == d.degree` を返すように定義されています。`!d` は否定を作成することに注意してください。詳細は [`filter_terms`](@ref) を参照してください。

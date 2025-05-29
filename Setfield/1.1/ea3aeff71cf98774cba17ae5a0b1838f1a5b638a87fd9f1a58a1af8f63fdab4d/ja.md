```
@lens
```

フィールドアクセスからレンズを構築します。

# 例

```jldoctest
julia> using Setfield

julia> struct T;a;b;end

julia> t = T("A1", T(T("A3", "B3"), "B2"))
T("A1", T(T("A3", "B3"), "B2"))

julia> l = @lens _.b.a.b
(@lens _.b.a.b)

julia> get(t, l)
"B3"

julia> set(t, l, 100)
T("A1", T(T("A3", 100), "B2"))

julia> t = ("one", "two")
("one", "two")

julia> set(t, (@lens _[1]), "1")
("1", "two")

julia> # インデックスは常に外部スコープで評価されます; プロパティの場合は、補間を使用できます:
       n, i = :a, 10
       @lens(_.$n[i, i+1])
(@lens _.a[10, 11])
```

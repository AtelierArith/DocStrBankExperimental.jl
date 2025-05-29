```
ToField(f) :: Setter
```

`f`を設定する際に適用します。`f`が`Lens`の場合は`x -> get(x, f)`を使用してください。

# 例

```jldoctest
julia> using Setfield, Kaleido

julia> setter = (@lens _.x) ∘ ToField(@lens _.a)
(@lens _.x) ∘ (←(@lens _.a)|❌→)

julia> set((x = 1, y = 2), setter, (a = 10, b = 20))
(x = 10, y = 2)
```

```
ChainTransform(transforms)
```

入力に一連の変換 `ts` を適用する変換です。

変換 `first(ts)` が最初に適用されます。

# 例

```jldoctest
julia> l = rand(); A = rand(3, 4); t1 = ScaleTransform(l); t2 = LinearTransform(A);

julia> X = rand(4, 10);

julia> map(ChainTransform([t1, t2]), ColVecs(X)) == ColVecs(A * (l .* X))
true

julia> map(t2 ∘ t1, ColVecs(X)) == ColVecs(A * (l .* X))
true
```

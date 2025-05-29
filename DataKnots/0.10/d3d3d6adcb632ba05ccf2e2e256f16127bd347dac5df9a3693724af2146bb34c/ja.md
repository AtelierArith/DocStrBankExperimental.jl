```
 Max(X) :: クエリ
```

組み合わせ形式では、`Max(X)`は`X`によって生成された要素の中から最大値を見つけます。

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[Max(X)]
┼───┼
│ 3 │
```

空の入力の`Max`は空です。

```jldoctest
julia> unitknot[Max(Int[])]
(empty)
```

---

```
Each(X >> Max) :: クエリ
```

クエリ形式では、`Max`はその入力要素の最大値を見つけます。

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[X >> Max]
┼───┼
│ 3 │
```

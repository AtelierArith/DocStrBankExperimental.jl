```
 Min(X) :: Query
```

組み合わせ形式では、`Min(X)`は`X`によって生成された要素の中から最小値を見つけます。

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[Min(X)]
┼───┼
│ 1 │
```

空の入力の`Min`は空です。

```jldoctest
julia> unitknot[Min(Int[])]
(empty)
```

---

```
Each(X >> Min) :: Query
```

クエリ形式では、`Min`はその入力要素の最小値を見つけます。

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[X >> Min]
┼───┼
│ 1 │
```

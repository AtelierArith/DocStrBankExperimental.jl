```
Sum(X) :: Query
```

組み合わせ形式では、`Sum(X)`は`X`によって生成された要素の合計を出力します。

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[Sum(X)]
┼───┼
│ 6 │
```

空の入力の`Sum`は`0`です。

```jldoctest
julia> unitknot[Sum(Int[])]
┼───┼
│ 0 │
```

---

```
Each(X >> Sum) :: Query
```

クエリ形式では、`Sum`は入力要素の合計を出力します。

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[X >> Sum]
┼───┼
│ 6 │
```

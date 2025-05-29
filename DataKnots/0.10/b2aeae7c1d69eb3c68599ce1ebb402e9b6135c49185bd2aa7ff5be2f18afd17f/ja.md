```
Count(X) :: Query
```

組み合わせ形式では、`Count(X)`は`X`によって生成された要素の数を出力します。

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[Count(X)]
┼───┼
│ 3 │
```

---

```
Each(X >> Count) :: Query
```

クエリ形式では、`Count`はその入力の要素の数を出力します。

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[X >> Count]
┼───┼
│ 3 │
```

集約の範囲を制限するには、`Each`を使用します。

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[Lift(1:3) >> Each(X >> Count)]
──┼───┼
1 │ 3 │
2 │ 3 │
3 │ 3 │
```

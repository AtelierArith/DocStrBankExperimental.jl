```
Last(X) :: Query
```

組み合わせ形式では、`Last(X)`はその引数`X`によって生成された最後の要素を出力します。

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[Last(X)]
┼───┼
│ c │
```

---

```
Each(X >> Last) :: Query
```

クエリ形式では、`Last`はその入力の最後の要素を出力します。

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[X >> Last]
┼───┼
│ c │
```

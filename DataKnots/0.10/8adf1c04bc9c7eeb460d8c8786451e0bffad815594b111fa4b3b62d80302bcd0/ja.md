```
Nth(X, N) :: Query
```

組み合わせ形式では、`Nth(X, N)`は引数`X`によって生成された`N`番目の要素を出力します。

```jldoctest
julia> X = Lift('a':'d');

julia> N = Count(X) .÷ 2;

julia> unitknot[Nth(X, N)]
┼───┼
│ b │
```

---

```
Each(X >> Nth(N)) :: Query
```

クエリ形式では、`Nth(N)`はその入力によって生成された`N`番目の要素を出力します。

```jldoctest
julia> X = Lift('a':'d');

julia> N = Count(X) .÷ 2;

julia> unitknot[X >> Nth(N)]
┼───┼
│ b │
```

```
First(X) :: Query
```

組み合わせ形式では、`First(X)`はその引数`X`によって生成された最初の要素を出力します。

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[First(X)]
┼───┼
│ a │
```

---

```
Each(X >> First) :: Query
```

クエリ形式では、`First`はその入力の最初の要素を出力します。

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[X >> First]
┼───┼
│ a │
```

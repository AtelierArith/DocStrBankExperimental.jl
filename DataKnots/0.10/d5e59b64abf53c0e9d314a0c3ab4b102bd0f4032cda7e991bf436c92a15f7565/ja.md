```
Exists(X) :: Query
```

組み合わせ形式では、`Exists(X)`は`X`が要素を生成するかどうかをテストするブール値を出力します。

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[Exists(X)]
┼──────┼
│ true │
```

クエリ引数`X`が空の場合、`Exists(X)`は`false`を生成します。

```jldoctest
julia> X = Lift([]);

julia> unitknot[Exists(X)]
┼───────┼
│ false │
```

---

```
Each(X >> Exists) :: Query
```

クエリ形式では、`Exists`はその入力に要素があるかどうかをテストするブール値を出力します。

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[X >> Exists]
┼──────┼
│ true │
```

クエリ入力が空の場合、`Exists`は`false`を生成します。

```jldoctest
julia> X = Lift([]);

julia> unitknot[X >> Exists]
┼───────┼
│ false │
```

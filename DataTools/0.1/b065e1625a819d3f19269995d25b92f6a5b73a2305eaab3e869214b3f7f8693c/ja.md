```
rightif(predicate, [focus = identity]) -> op::Function
```

最初の引数を保持するバイナリ関数を返します。ただし、`predicate`が`true`に評価される場合は除きます。

これは次のように同等です。

```julia
(l, r) -> predicate(focus(l), focus(r)) ? r : l
```

# 例

```jldoctest
julia> using DataTools, Transducers

julia> table = 1:100 |> Map(x -> (k = gcd(x, 42), v = x));

julia> table |> Take(5) |> collect  # プレビュー
5-element Array{NamedTuple{(:k, :v),Tuple{Int64,Int64}},1}:
 (k = 1, v = 1)
 (k = 2, v = 2)
 (k = 3, v = 3)
 (k = 2, v = 4)
 (k = 1, v = 5)

julia> foldl(rightif(<), Map(x -> x.k), table)  # 最大値
42

julia> foldl(rightif(>), Map(x -> x.k), table)  # 最小値
1

julia> foldl(rightif(<, x -> x.k), table)   # 最初の最大値
(k = 42, v = 42)

julia> foldl(rightif(<=, x -> x.k), table)  # 最後の最大値
(k = 42, v = 84)

julia> foldl(rightif(>, x -> x.k), table)   # 最初の最小値
(k = 1, v = 1)

julia> foldl(rightif(>=, x -> x.k), table)  # 最後の最小値
(k = 1, v = 97)

julia> table |> Scan(rightif(<, x -> x.k)) |> Take(5) |> collect
5-element Array{NamedTuple{(:k, :v),Tuple{Int64,Int64}},1}:
 (k = 1, v = 1)
 (k = 2, v = 2)
 (k = 3, v = 3)
 (k = 3, v = 3)
 (k = 3, v = 3)
```

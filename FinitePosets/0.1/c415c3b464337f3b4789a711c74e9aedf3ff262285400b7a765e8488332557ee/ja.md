`Poset(f::Function,e::AbstractVector)`

は、要素 `e` を持ち、2つの要素間の順序を関数 `f` によって与える `Poset` を作成します。

```julia-repl
julia> Poset((x,y)->all(x.≤y),vec(collect(Iterators.product(1:2,1:3))))
(1, 1)<(2, 1)<(2, 2)<(2, 3)
(1, 1)<(1, 2)<(2, 2)
(1, 2)<(1, 3)<(2, 3)
```

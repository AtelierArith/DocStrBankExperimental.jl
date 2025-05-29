```
breakeven(yield, cashflows::Vector)
breakeven(yield, cashflows::Vector,times::Vector)
```

与えられた利回りで累積キャッシュフローがブレークイーブンになる時点を計算します。

前提条件:

  * キャッシュフローは期間の終わりに発生します
  * キャッシュフローは均等に間隔を置いて発生し、`times`が指定されていない場合は最初のものが時刻ゼロで発生します

キャッシュフローの流れが決してブレークイーブンにならない場合は`nothing`を返します。

```julia
julia> breakeven(0.10, [-10,1,2,3,4,8])
5

julia> breakeven(0.10, [-10,15,2,3,4,8])
1

julia> breakeven(0.10, [-10,-15,2,3,4,8]) # `nothing`値を返します


```

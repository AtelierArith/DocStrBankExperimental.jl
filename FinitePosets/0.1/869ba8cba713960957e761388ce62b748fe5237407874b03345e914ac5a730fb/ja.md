  * `Poset(:chain,e)`  要素 `e` を持つチェーン
  * `Poset(:antichain,e)`  要素 `e` を持つアンチチェーン
  * `Poset(:powerset,n::Integer)`  包含を持つ集合 `1:n` の冪集合

```julia-repl
julia> p=Poset(:powerset,3);p.show_element=(io,p,n)->join(io,p.elements[n]);

julia> p
<1<12<123
<2<12
<3<13<123
1<13
2<23<123
3<23
```

  * `Poset(:powerset,e)`  包含を持つ集合 `e` の冪集合
  * `Poset(:partitionsdominance,n)`  優越順序を持つ `n` の分割のポセット

```julia-repl
julia> Poset(:partitionsdominance,5)
[1, 1, 1, 1, 1]<[2, 1, 1, 1]<[2, 2, 1]<[3, 1, 1]<[3, 2]<[4, 1]<[5]
```

  * `Poset(:chain,e)`  a chain with elements `e`
  * `Poset(:antichain,e)`  an antichain with elements `e`
  * `Poset(:powerset,n::Integer)`  the powerset of the set `1:n` with inclusion

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

  * `Poset(:powerset,e)`  the powerset of the set `e` with inclusion
  * `Poset(:partitionsdominance,n)`  the poset of partitions of `n` with dominance order

```julia-repl
julia> Poset(:partitionsdominance,5)
[1, 1, 1, 1, 1]<[2, 1, 1, 1]<[2, 2, 1]<[3, 1, 1]<[3, 2]<[4, 1]<[5]
```

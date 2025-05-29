`closed_subsystems(W)` 

`W`  should  be  a  Weyl  group.  The  function returns the Poset of closed subsystems  of the root system of `W`. Each closed subsystem is represented by  the list of indices of its simple roots.  If `W` is the Weyl group of a reductive  group  `𝐆`,  then  closed  subsystem  correspond  to reductive subgroups of maximal rank. And all such groups are obtained this way, apart from  some  exceptions  in  characteristics  2  and 3 (see [Malle-Testerman 2011](biblio.htm#MT11) Proposition 13.4).

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> closed_subsystems(W)
1 2<1 4<4<∅
1 2<1 5<1<∅
1 2<2 6<6<∅
1 2<3 5<5<∅
1 4<1
1 5<6
1 5<5
2 6<2<∅
3 5<3<∅
```

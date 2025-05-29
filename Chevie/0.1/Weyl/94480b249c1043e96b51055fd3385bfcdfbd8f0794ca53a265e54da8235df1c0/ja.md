`highest_short_root(W)`

`W` が不可約コクセター群でない場合はエラーです。そうでなければ、`HighestShortRoot` は `W` の最大の高さを持つ唯一の短根のインデックスを返します。すべての根が同じ長さである場合、これは最大の高さを持つ唯一の根のインデックスであり、`nref(W)` に等しくなります。

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> highest_short_root(W)
4
```

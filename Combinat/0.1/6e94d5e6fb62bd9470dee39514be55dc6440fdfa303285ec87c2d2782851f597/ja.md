`primitiveroot(m::Integer)`   は   原始根を返します。すなわち、`mod. m` で  `prime_residues(m)` を乗法的に生成します。この関数は、`mod. m` に原始根が存在しない場合は `nothing` を返します。

原始根は、`m` が `4` または `p^a` または `2p^a` である場合に存在します（ここで、`p` は 2 より大きい素数です）。

```julia-repl
julia> primitiveroot(23)
5
```

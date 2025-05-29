```
find_similarity_transform(sys1, sys2, method = :obsv)
```

`ControlSystemsBase.similarity_transform(sys1, T) == sys2` となるような T を見つけます。

参考文献: 線形システム理論における最小状態空間実現の概要, B. De Schutter

`method == :obsv` の場合、`sys1` と `sys2` の可観測行列を使用して T を見つけます。一方、`method == :ctrb` は制御可能行列を使用します。

```jldoctest
julia> T = randn(3,3);

julia> sys1 = ssrand(1,1,3);

julia> sys2 = ControlSystemsBase.similarity_transform(sys1, T);

julia> T2 = find_similarity_transform(sys1, sys2);

julia> T2 ≈ T
true
```

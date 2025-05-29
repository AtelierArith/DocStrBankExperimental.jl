```
≪(a::AbstractInterval, b::AbstractInterval) -> Bool
less_than_disjoint(a::AbstractInterval, b::AbstractInterval) -> Bool
```

小さいかつ非重複の比較演算子。`a`が`b`より小さく、かつ重複していない場合は`true`を返します（重複していない）。

```
julia> 0..10 ≪ 10..20
false

julia> 0..10 ≪ 11..20
true
```

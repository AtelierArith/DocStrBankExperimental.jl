```
onbounds(loc::T, bounds::Bounds{T}) where T<:Union{LLA,ENU}
```

位置 `loc` が `bounds` の境界上にあるかどうかを確認します。これは、inbounds テストを通過したポイントにのみ機能します。

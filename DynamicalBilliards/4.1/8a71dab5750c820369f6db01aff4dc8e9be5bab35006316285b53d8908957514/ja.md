```
Disk{T<:AbstractFloat}  <: Circular{T}
```

円に外側の伝播が許可されたディスク状の障害物（不変型）。

### フィールド:

  * `c::SVector{2,T}` : 中心。
  * `r::T` : 半径。
  * `name::String` : ユーザーの便宜のために付けられた名前。デフォルトは「Disk」。

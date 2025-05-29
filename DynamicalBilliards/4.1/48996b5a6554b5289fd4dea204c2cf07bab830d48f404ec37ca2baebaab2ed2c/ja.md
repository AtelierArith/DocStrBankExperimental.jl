```
Semicircle{T<:AbstractFloat} <: Circular{T}
```

半円を表す障害物。伝播は半円の内部のみで許可されます。

### フィールド:

  * `c::SVector{2,T}` : 中心。
  * `r::T` : 半径。
  * `facedir::SVector{2,T}` : 半円の開いた面が向いている方向。
  * `name::String` : ユーザーの便宜のために与えられた障害物の名前。デフォルトは「Semicircle」です。

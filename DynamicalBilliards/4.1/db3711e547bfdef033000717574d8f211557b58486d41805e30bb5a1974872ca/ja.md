```
RandomDisk{T<:AbstractFloat} <: Circular{T}
```

円盤のような障害物で、衝突する粒子をランダム（かつ均等に）反射します。円の外側での伝播が許可されています。

### フィールド:

  * `c::SVector{2,T}` : 中心。
  * `r::T` : 半径。
  * `name::String` : ユーザーの便宜のために付けられた名前。デフォルトは「Random disk」です。

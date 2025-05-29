```
SplitterWall{T<:AbstractFloat} <: Wall{T}
```

光線を分割することを許可する壁の障害物（可変型）。

### フィールド:

  * `sp::SVector{2,T}` : 壁の始点。
  * `ep::SVector{2,T}` : 壁の終点。
  * `normal::SVector{2,T}` : 壁に対する法線ベクトルで、粒子が衝突する前に「どこから来るか」を指し示します。ベクトルの大きさは無関係です。
  * `pflag::Bool` : 粒子が現在どこに伝播しているかを追跡するフラグ（`pflag` = 伝播フラグ）。`true` は壁が初期化されたときの `normal` ベクトルに関連付けられています。デフォルトは `true` です。
  * `name::String` : ユーザーの便宜のために与えられた障害物の名前。デフォルトは "Splitter wall" です。

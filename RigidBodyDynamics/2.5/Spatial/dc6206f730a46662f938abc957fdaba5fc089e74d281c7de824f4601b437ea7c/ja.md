```julia
SpatialInertia(frame, moment, cross_part, mass)

```

`SpatialInertia`を構築するには、次のように指定します：

  * `frame`: 空間慣性が表現されるフレーム。
  * `moment`: `frame`で表現された慣性モーメント（すなわち、`frame`の軸に沿っており、`frame`の原点を中心とする）。
  * `cross_part`: フレームで表現された質量中心に質量を掛けたもの。
  * `mass`: 総質量。

`SpatialInertia`のより便利な構築のために、キーワード引数コンストラクタの使用を検討してください。

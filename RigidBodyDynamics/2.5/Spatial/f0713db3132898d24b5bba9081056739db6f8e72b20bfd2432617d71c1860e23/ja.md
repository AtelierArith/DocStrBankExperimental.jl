```julia
SpatialInertia(frame; moment, moment_about_com, com, mass)

```

`SpatialInertia`を次のように指定して構築します：

  * `frame`: 空間慣性が表現されるフレーム。
  * 次のいずれか：

      * `moment`: `frame`で表現された慣性モーメント（すなわち、`frame`の原点周りおよび`frame`の軸において）。
      * `moment_about_com`: 質量中心周りの慣性モーメント、`frame`の軸において。
  * `com`: `frame`で表現された質量中心。
  * `mass`: 総質量。

`com`および`mass`のキーワード引数は必須であり、`moment`と`moment_about_com`のうち正確に1つが必要です。

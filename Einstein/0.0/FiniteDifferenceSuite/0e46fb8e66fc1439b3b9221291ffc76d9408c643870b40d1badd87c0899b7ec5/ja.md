```
LocalBarycentricInterpolation(points, values; degree=4)
```

等間隔データポイントのための局所バリセントリックラグランジュ補間子を構築します。

均等に間隔を空けたポイント `points` でのデータ `values` を使用して、次数 `degree` の多項式近似を作成します。補間は、評価点に最も近い `degree + 1` ポイントを使用して局所的に行われます。

# 引数

  * `points::StepRangeLen{TF}`: 補間のための等間隔ポイント
  * `values::AbstractVector{TF}`: ポイントでの関数値
  * `degree::Integer=4`: 局所多項式補間子の次数

# 戻り値

  * `[minimum(points), maximum(points)]` 内の任意のポイントで評価できる補間関数

# 注意事項

  * `length(points) >= degree + 1` が必要です
  * `points` と `values` は同じ長さでなければなりません
  * 数値的安定性のためにバリセントリックラグランジュ補間を使用します

# 参考文献

  * [Berrut2004](@citet*)

```
RateCurve{F, R <: Real, I <: DataInterpolations.AbstractInterpolation} <: AbstractRateCurve
```

入力割引ファクターから導出されたゼロレートに基づく補間されたレートカーブを表します。

# フィールド

  * `reference_date::R`: カーブの基準日で、内部ティック単位（例：エポックからのミリ秒）で表されます。
  * `interpolator::I`: 年の分数の関数としてゼロレートカーブを表す補間オブジェクト（`DataInterpolations.jl`から）。
  * `builder::F`: 補間器を再構築するために使用される関数 `(u, t) -> interpolator` で、ここで `u` はゼロレート、`t` は年の分数です。

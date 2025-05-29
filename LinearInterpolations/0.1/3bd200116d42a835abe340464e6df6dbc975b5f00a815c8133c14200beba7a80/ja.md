```
itp = Interpolate(axes, values; combine = LinearInterpolations.combine, extrapolate = :error)
```

与えられた引数から `Interpolate` を作成します。補間 `itp` は点で評価できます。例: `itp([1,2])`。

# 引数

  * axes: グリッドポイントの座標。
  * values: 各軸の長さと一貫性のあるサイズを持つ AbstractArray。
  * extrapolate: グリッドの制限外の点での補間の動作。可能な値は次のとおりです：

      * [`Replicate`](@ref), `:replicate`
      * [`Reflect`](@ref), `:reflect`
      * [`Error`](@ref), `:error`
      * [`Fuzzy`](@ref), `:fuzzy`
      * [`WithPoint`](@ref)
      * [`Constant`](@ref)
  * combine: 重みと値を最終結果に組み合わせるカスタム関数。

[`LinearInterpolations.combine`](@ref) を参照してください。

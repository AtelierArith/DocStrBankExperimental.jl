```
computecalibration(preds::AbstractVector{<:Normal}, truevals::AbstractVector{<:Real}; pvals)
computecalibration(preds::AbstractVector{<:MvNormal}, truevals::AbstractVector{<:AbstractVector{<:Real}}; pvals)
```

中央予測セットを使用して、一連の真の観測値に対して予測された（単変量または多変量）正規分布のキャリブレーションを計算します。

名前付きタプル `(; pvals, calibrationvals)` を返します。予測が適切にキャリブレーションされている場合、すべてのインデックスに対して `pvals ≈ calibrationvals` となります。`plot(pvals, calibrationvals)` をプロットすると、(0, 0) から (1, 1) までの直線が得られるはずです。

# kwargs

  * `pvals`: カバレッジを評価する確率。デフォルトは `0:0.05:1` です。

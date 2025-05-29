```
imanalytic(::Type{<:AbstractModel})
```

モデルが画像領域で点ごとに解析的であるかどうかを判断します。つまり、任意の点でその強度を評価できるかどうかです。`IsAnalytic()` が真であれば、強度を計算するために `intensity_point` を呼び出そうとします。

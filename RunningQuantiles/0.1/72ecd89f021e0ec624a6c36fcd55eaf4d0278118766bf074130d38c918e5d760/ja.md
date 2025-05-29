```
result = running_quantile(v, p, w, nan_mode=SkipNaNs())
```

ベクトル `v` の `p`-th 分位数をウィンドウ `w` で計算します。ここで、`w` は奇数のウィンドウ長またはオフセットの範囲です。具体的には、

  * `w` が `AbstractUnitRange` の場合、`result[i]` は `v[(i .+ w) ∩ eachindex(v)]` の `p`-th 分位数であり、`NaN` は `nan_mode` に従って処理されます：

      * `nan_mode==SkipNaN()`: `NaN` 値は無視され、非 `NaN` の値に対して分位数が計算されます
      * `nan_mode==PropagateNaNs()`: 入力ウィンドウに `NaN` が含まれている場合、結果は `NaN` になります
      * `nan_mode==ErrOnNaN()`: 入力ウィンドウのいずれかに `NaN` が含まれている場合、エラーが発生します
  * `w` が奇数の整数の場合、長さ `w` の中心ウィンドウが使用され、すなわち `-w÷2:w÷2` です

```
